# Sealgraf

**Every dollar, seen and sealed.**

Sealgraf checks agent purchases against the owner's limits and seals a receipt anyone can check.

Sealgraf is the approval layer for AI agent spending. Before an agent buys something, it asks Sealgraf. Sealgraf checks the purchase against the spending limits the owner set, asks the owner to approve anything above the ask line, and — once the purchase is reported — seals a tamper-evident receipt that anyone can verify. Sealgraf never moves money: it records the decision and the evidence.

This repository holds the documentation and connection configuration for the hosted Sealgraf MCP server. The server itself is operated at [sealgraf.com](https://sealgraf.com); its source code is not published here.

## Connect

- **Endpoint:** `https://sealgraf.com/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth 2.1 — sign in, set your spending limits, and approve the connection. Dynamic client registration is supported; no API key or client secret is needed for MCP connections.

Generic MCP client configuration:

```json
{
  "mcpServers": {
    "sealgraf": {
      "url": "https://sealgraf.com/mcp"
    }
  }
}
```

Client-specific snippets are in [examples/](examples/). Step-by-step guides for Claude, ChatGPT, Cursor, VS Code, Mistral Vibe, and more are on the [integrations page](https://sealgraf.com/integrations).

## Tools

| Tool | What it does |
| --- | --- |
| `check_permission` | Check a planned purchase against the owner's limits before buying. Returns allowed, denied, or needs-approval. |
| `check_status` | Check where a pending approval stands. |
| `report_purchase` | Report a completed purchase so Sealgraf can seal the receipt. |
| `get_receipt` | Fetch a sealed receipt for a purchase. |

## How a purchase flows

1. The agent checks the purchase with Sealgraf before buying.
2. Within the owner's limits, it is allowed right away. Above the ask line, Sealgraf asks the owner.
3. The owner approves or declines in Sealgraf.
4. After buying, the agent reports the purchase and Sealgraf seals the receipt.
5. Anyone with the receipt's check link can verify it was sealed — no account needed.

## Links

- Website: https://sealgraf.com
- Integrations: https://sealgraf.com/integrations
- Official MCP Registry: `com.sealgraf/sealgraf`

## License

The contents of this repository (documentation and configuration examples) are released under the MIT License. The hosted Sealgraf service is governed by the terms at https://sealgraf.com/legal/terms.
