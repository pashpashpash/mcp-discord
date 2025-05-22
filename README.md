# Discord MCP Server

A Model Context Protocol (MCP) server that provides Discord integration capabilities to MCP clients like Claude Desktop.

<a href="https://glama.ai/mcp/servers/wvwjgcnppa"><img width="380" height="200" src="https://glama.ai/mcp/servers/wvwjgcnppa/badge" alt="mcp-discord MCP server" /></a>

## Features

### Server Information
- `get_server_info`: Get detailed server information
- `list_members`: List server members and their roles

### Message Management
- `send_message`: Send a message to a channel
- `read_messages`: Read recent message history
- `add_reaction`: Add a reaction to a message
- `add_multiple_reactions`: Add multiple reactions to a message
- `remove_reaction`: Remove a reaction from a message
- `moderate_message`: Delete messages and timeout users

### Channel Management
- `create_text_channel`: Create a new text channel
- `delete_channel`: Delete an existing channel

### Role Management
- `add_role`: Add a role to a user
- `remove_role`: Remove a role from a user

### Webhook Management
- `create_webhook`: Create a new webhook
- `list_webhooks`: List webhooks in a channel
- `send_webhook_message`: Send messages via webhook
- `modify_webhook`: Update webhook settings
- `delete_webhook`: Delete a webhook

## Prerequisites

1. **Set up your Discord bot**:
   - Create a new application at [Discord Developer Portal](https://discord.com/developers/applications)
   - Create a bot and copy the token
   - Enable required privileged intents:
     - MESSAGE CONTENT INTENT
     - PRESENCE INTENT
     - SERVER MEMBERS INTENT
   - Invite the bot to your server using OAuth2 URL Generator

2. **Python Requirements**:
   - Python 3.8 or higher
   - pip (Python package installer)

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/pashpashpash/mcp-discord.git
   cd mcp-discord
   ```

2. **Create and Activate Virtual Environment**:
   ```bash
   # On Windows
   python -m venv venv
   venv\Scripts\activate

   # On macOS/Linux
   python -m venv venv
   source venv/bin/activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install -e .
   ```
   Note: If using Python 3.13+, also install audioop: `pip install audioop-lts`

4. **Configure Claude Desktop**:

Add this to your claude_desktop_config.json:
- macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "discord": {
      "command": "python",
      "args": ["-m", "mcp-discord"],
      "cwd": "path/to/mcp-discord",
      "env": {
        "DISCORD_TOKEN": "your_bot_token"
      }
    }
  }
}
```
Note: 
- Replace "path/to/mcp-discord" with the actual path to your cloned repository
- Replace "your_bot_token" with your Discord bot token

## Debugging

If you run into issues, check Claude Desktop's MCP logs:
```bash
tail -n 20 -f ~/Library/Logs/Claude/mcp*.log
```

Common issues:
1. **Token Errors**:
   - Verify your Discord bot token is correct
   - Check that all required intents are enabled

2. **Permission Issues**:
   - Ensure the bot has proper permissions in your Discord server
   - Verify the bot's role hierarchy for role management commands

3. **Installation Issues**:
   - Make sure you're using the correct Python version
   - Try recreating the virtual environment
   - Check that all dependencies are installed correctly

## License

MIT License - see LICENSE file for details.

---
Note: This is a fork of the [original mcp-discord repository](https://github.com/hanweg/mcp-discord).
