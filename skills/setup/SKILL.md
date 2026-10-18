---
name: setup
description: Connect a user's own Falatu account to Claude and verify the Falatu MCP connection. Use for initial setup, reconnecting, or checking which account is connected.
---

Connect through the packaged Falatu MCP server at `https://mcp.falatu.ai/mcp`.

When Falatu tools are available, call `get_account` to verify the authenticated account and permissions. If sign-in is required or the connection is missing, guide the user to the Falatu connector's Connect action in Claude and browser authorization flow. They sign in with their own Falatu account and review the requested access there. Do not ask them to paste passwords or tokens into chat, read local credential stores, or replace global MCP configuration.

After authorization, retry `get_account`. Report only the account returned by the tool. OAuth currently uses the first accessible organization and tools do not accept an organization selector. If the returned account is not the intended one, stop and help the user connect the correct account. Run `list_automations` as a read-only connection check. Do not create or activate anything during setup.

A Falatu account and a connected Instagram account are separate requirements. If Instagram is not connected, direct the user to Falatu's account settings using the app link returned by the server. Do not claim Instagram is connected from OAuth sign-in alone.

Report success only after an authenticated tool call succeeds. For authorization, permission, or connection errors, explain the specific next step and stop dependent actions. Members have read-only access; writes require owner/admin permissions and the write scope. Do not try to bypass a denied permission.

Respond in the user's language. Finish by showing the connected account, returned workspace, connection-check result, and one relevant next action.
