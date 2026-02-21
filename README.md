# TC Chat

A fast, modern IRC web client built with Rust and SolidJS.

## Architecture

```
┌─────────────────────────────────────────────────┐
│                   Browser                       │
│  ┌─────────────────────────────────────────┐    │
│  │     SolidJS + TanStack Virtual          │    │
│  │     - Virtual scrolling (only visible)  │    │
│  │     - Fine-grained reactivity           │    │
│  └─────────────────┬───────────────────────┘    │
└────────────────────┼────────────────────────────┘
                     │ WebSocket
┌────────────────────┼────────────────────────────┐
│    Rust Backend    ▼                            │
│  ┌─────────────────────────────────────────┐    │
│  │  Axum Web Server                        │    │
│  │  - REST API + WebSocket                 │    │
│  ├─────────────────────────────────────────┤    │
│  │  IRC Engine                             │    │
│  │  - Multiple connections                 │    │
│  │  - SPGROUPS/SPJOIN support              │    │
│  ├─────────────────────────────────────────┤    │
│  │  SQLite + FTS5                          │    │
│  │  - Message storage                      │    │
│  │  - Instant full-text search             │    │
│  └─────────────────────────────────────────┘    │
└─────────────────────────────────────────────────┘
```

## Features

- **Virtual scrolling** - Handles 100k+ messages smoothly
- **Instant search** - SQLite FTS5 full-text search
- **Always-on** - Server maintains IRC connections

