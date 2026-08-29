# PostZen plugin for Claude Code

Schedule and publish social media posts across 10 platforms — X (Twitter), Instagram, TikTok, LinkedIn, Facebook, YouTube, Threads, Pinterest, Bluesky, and Telegram — without leaving Claude Code.

The plugin connects to the hosted [PostZen MCP server](https://mcp.postzen.dev) and adds workflow skills on top of it.

## What you get

- **`/postzen:post`** — draft, adapt, and publish or schedule a post across platforms, with media uploads, queue slots, and best-time-to-post suggestions.
- **`/postzen:analytics`** — a readable analytics summary: post performance, follower growth, daily metrics.
- **`/postzen:connect`** — guided flow to link a new social account.
- **35+ MCP tools** for everything else: queue management, Pinterest boards, webhooks, profiles, media presigns, and more. Claude picks these up automatically.

## Install

```bash
claude plugin install postzen@claude-community
```

Then authenticate: run `/mcp` in a session, select **postzen**, and click **Authenticate**. You'll be sent to the PostZen dashboard to approve access (and choose which profiles to expose), then bounced back automatically.

Don't have a PostZen account? Sign up at [postzen.dev](https://www.postzen.dev) and connect your social accounts in the [dashboard](https://app.postzen.dev) — or let Claude walk you through it with `/postzen:connect`.

### Headless / CI use

For non-interactive environments, skip OAuth and pass an API key (create one in the dashboard under Settings → API keys):

```bash
claude mcp add --transport http postzen https://mcp.postzen.dev/mcp \
  --header "Authorization: Bearer $POSTZEN_API_KEY"
```

## Example prompts

- "Post this launch announcement to X and LinkedIn tomorrow at 9am PT"
- "Take this blog post and turn it into a thread for X and a LinkedIn post, save both as drafts"
- "How did my posts perform this week?"
- "Add these three posts to my queue"
- "Connect my Pinterest account"

## Safety

Publishing is an outward-facing action: the skills always show you the final per-platform content and timing and ask for confirmation before anything goes live. Drafts never require confirmation.

## Development

```bash
git clone https://github.com/postzen-dev/postzen-claude-plugin
claude --plugin-dir ./postzen-claude-plugin
```

Run `/reload-plugins` after editing to pick up changes, and `claude plugin validate ./postzen-claude-plugin` before submitting.

## Links

- [PostZen](https://www.postzen.dev) · [Dashboard](https://app.postzen.dev) · [API docs](https://docs.postzen.dev) · [Status](https://status.postzen.dev)
- Prefer a raw API? See the [agent quickstart](https://www.postzen.dev/agent-quickstart.md), the [Node SDK](https://www.npmjs.com/package/@postzen/node), [Python SDK](https://pypi.org/project/postzen-sdk/), or [CLI](https://www.npmjs.com/package/@postzen/cli).

## License

MIT
