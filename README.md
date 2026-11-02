<p align="center"><img src="logo-512.png" width="96" alt="The Charter Desk"></p>

# The Charter Desk MCP server

[![mcptry](https://mcptry.com/badge/com.thecharterdesk/yacht-charter)](https://mcptry.com/servers/com.thecharterdesk/yacht-charter)

Live yacht charter inventory for AI assistants: 9,000+ sailboats, catamarans, motor yachts, gulets and houseboats from 800+ operators in 50 countries, with live prices, real availability and deals. Ask for a boat by place, dates and group size, compare prices, and request a written quote from [The Charter Desk](https://thecharterdesk.com).

- **Endpoint:** `https://thecharterdesk.com/mcp` (Streamable HTTP, remote, nothing to install)
- **Docs:** [thecharterdesk.com/mcp/docs](https://thecharterdesk.com/mcp/docs), generated from the server itself
- **Registry:** `com.thecharterdesk/yacht-charter` in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers/com.thecharterdesk%2Fyacht-charter/versions/latest)
- **Auth:** none. The four read tools need no sign-in. `request_quote` needs the guest's own email or phone, passed by the assistant, or a session from an earlier answer; a guest can also sign in with OAuth (a code sent to their email).

## Tools

| Tool | What it does | Kind |
|---|---|---|
| `search_yachts` | Search yachts by destination, dates, group size and boat type, with live prices and availability | read |
| `get_yacht` | One yacht's full details: cabins, extras, deposit, check-in days and free weeks | read |
| `price_range` | Price ranges for a destination and season | read |
| `best_deals` | Real discounts and last-minute deals on upcoming departures | read |
| `request_quote` | Asks the desk for a formal quote on one or more yachts. The desk sends a written quote, with every cost on it, to the guest's own email or phone. Nothing is booked or paid; the guest confirms the booking with the desk. | write |

## Try it

- "Find a catamaran in Croatia for 8 people, first week of July"
- "What are the best yacht deals in Greece next month?"
- "How much does a week on a sailboat in the British Virgin Islands cost in March?"
- "Find me a skippered gulet in Turkey for a family of 6 in August"

## Connect

**Claude (claude.ai / Desktop):** Settings → Connectors → Add custom connector → `https://thecharterdesk.com/mcp`

**Claude Code:**
```sh
claude mcp add --transport http charterdesk https://thecharterdesk.com/mcp
```

**ChatGPT:** Settings → Apps & Connectors → Create → MCP server URL `https://thecharterdesk.com/mcp`

**Cursor** (`~/.cursor/mcp.json`):
```json
{ "mcpServers": { "charterdesk": { "url": "https://thecharterdesk.com/mcp" } } }
```

**VS Code** (`.vscode/mcp.json`):
```json
{ "servers": { "charterdesk": { "type": "http", "url": "https://thecharterdesk.com/mcp" } } }
```

**Any client that only speaks stdio:**
```sh
npx -y mcp-remote https://thecharterdesk.com/mcp
```

## Limits

Browsing without an email or phone returns up to 10 rows per answer, 30 calls per 10 minutes per address. With the guest's email, phone or session: up to 20 rows, 30 calls an hour. Up to 5 quote requests a day per person. Full limits on the [docs page](https://thecharterdesk.com/mcp/docs).

## Links

- Website: [thecharterdesk.com](https://thecharterdesk.com)
- Privacy: [thecharterdesk.com/legal/privacy](https://thecharterdesk.com/legal/privacy)
- Terms: [thecharterdesk.com/legal/terms](https://thecharterdesk.com/legal/terms)
- Support: admin@thecharterdesk.com

This repository holds the public listing for the hosted server only. The server runs at thecharterdesk.com.
