# RunDrill SQL

Your personal **SQL coach** inside your AI agent — built to teach you to **think in sets, not rows**,
the shift most SQL learners never quite make. Instead of watching a query get generated, you **read
it, predict the exact rows, predict the plan from `EXPLAIN`, and review it for bugs** — treating the
query planner and the error message as your teacher. Short targeted drills, an honest picture of your
level (novice → expert), and mistake memory that resurfaces what you got wrong. Your level and
progress live on the RunDrill MCP server (`mcp.rundrill.com`), synced across machines — not in a
local file.

**Why this course is different.** When an AI can write any query on demand, the real risk is the
*illusion of competence* — a query that runs and returns rows but is quietly wrong: it drops NULLs,
fans out a join, silently turns a `LEFT JOIN` inner, or won't use the index. RunDrill SQL trains
reading, predicting, and **reviewing** SQL. Its signature drill hands you plausible AI-written SQL
with a real defect (a `NOT IN` that breaks on a NULL, an `OFFSET` paginator that drifts, an SCD that
overwrites history) and asks you to find it — like a pull request.

The course climbs across engines: **SQLite** for the foundations, **PostgreSQL** from the middle on,
and an optional **Oracle & SQL Server dialects** track — plus specialization tracks for **analytics**,
**application backend**, and **data engineering**.

## One plugin, three hosts

The coaching skill (`skills/sql-coach/SKILL.md`) and `.mcp.json` are shared; each host reads its own
manifest and ignores the rest.

| Host | Reads |
|---|---|
| Claude Code / Claude Desktop | `.claude-plugin/plugin.json` + `.mcp.json` |
| OpenAI Codex | `.codex-plugin/plugin.json` + `.mcp.json` |
| Google Antigravity | `plugin.json` + `mcp_config.json` (+ `rules/`) |

The MCP endpoint is `https://mcp.rundrill.com/prog` — the programming-course host that SQL, Python,
and Rust share, passing `language: "sql"`. On first use the host opens a browser tab for the OAuth
handshake, then closes it — no API key to paste.

## Install

- **Claude Code / Desktop** — via the RunDrill marketplace:
  ```
  /plugin marketplace add rundrill/marketplace
  /plugin install rundrill-sql@rundrill
  ```
  Then run `/sql-coach`.
- **OpenAI Codex** — `codex plugin marketplace add rundrill/marketplace`, then install `rundrill-sql`.
- **Google Antigravity** — drop this folder into `~/.gemini/config/plugins/rundrill-sql/` (global)
  or `<workspace>/.agents/plugins/rundrill-sql/` (workspace-scoped).

## License & attribution

© RunDrill. Licensed under **Creative Commons Attribution-NonCommercial-NoDerivatives 4.0
International (CC BY-NC-ND 4.0)** — full text in [LICENSE](LICENSE). You may view, run, and share this
plugin unchanged, non-commercially, with attribution; you may not use it commercially or publish
modified/derivative versions. For other licensing, contact **hello@rundrill.com**.
