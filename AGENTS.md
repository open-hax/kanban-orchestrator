# Kanban Orchestrator — Agent Guidance

Contract-only kanban board orchestrator agent. No source code, no build step.

## What this is

Five EDN contract files that teach a knoxx-style agent runtime (e.g. Sol) about an agent whose purpose is to drive work by changing board state — never by editing code.

## Contracts

| File | Kind | Purpose |
|---|---|---|
| `contracts/agents/kanban_orchestrator.edn` | `:agent` | Agent definition: model, role, system prompt, context window |
| `contracts/roles/kanban_orchestrator.edn` | role | Role → capability mapping, permissions |
| `contracts/capabilities/cap_kanban_orchestrator.edn` | capability | Toolset (7 tools via rheos-kanban MCP) |
| `contracts/actors/kanban_orchestrator.edn` | actor | Actor binding to agent |
| `contracts/mcp_servers/rheos_kanban.edn` | `:mcp-server` | MCP server connection (HTTP transport) |

## Usage

Point a runtime at this directory as an extra contract root. The orchestrator agent, its role, capability, actor, and MCP server connection are all loaded from data.

## Toolset

- `project_glob`, `project_grep`, `project_read` — project inspection (read-only)
- `kanban_read_board`, `kanban_search_tasks`, `kanban_read_task` — board reads
- `kanban_update_status` — the only write surface

## License

GPL-3.0-or-later
