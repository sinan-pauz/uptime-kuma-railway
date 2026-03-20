# Deploy and Host Uptime Kuma on Railway

Uptime Kuma is an easy-to-use, self-hosted monitoring tool. It supports HTTP(s), TCP, DNS, Ping, and 20+ other monitor types with a reactive web UI. Get notified via Telegram, Discord, Slack, Email, and 90+ notification services when your services go down.

## About Hosting Uptime Kuma

Uptime Kuma runs as a single Docker container with no external database dependencies. It uses an embedded SQLite database stored in the `/app/data` directory, which must be backed by a persistent volume on Railway. The official `louislam/uptime-kuma:2` Docker image includes everything needed: Node.js runtime, a compiled Go healthcheck binary, and the web UI. The application listens on port 3001 and provides a responsive dashboard for configuring monitors, viewing uptime history, and managing status pages. On first launch, you create an admin account directly in the browser.

## Common Use Cases

- Monitor uptime and response times for websites, APIs, and TCP services
- Set up instant notifications via Telegram, Discord, Slack, or email when services go down
- Create public or private status pages for your users and team
- Track SSL certificate expiration dates and get alerts before they expire

## Dependencies for Uptime Kuma Hosting

- Persistent volume for SQLite database and configuration (minimum 1 GB recommended)
- Public networking enabled for the web UI (port 3001)

### Deployment Dependencies

- [Uptime Kuma GitHub Repository](https://github.com/louislam/uptime-kuma)
- [Uptime Kuma Documentation](https://github.com/louislam/uptime-kuma/wiki)
- [Uptime Kuma Docker Image](https://hub.docker.com/r/louislam/uptime-kuma)

### Implementation Details

The container uses a compiled Go binary (`extra/healthcheck`) for Docker health checks instead of HTTP-based checks. SQLite's default WAL journal mode may have issues with network-attached volumes — if you experience database locking errors, set the journal mode to `delete`.

## Why Deploy Uptime Kuma on Railway?

<!-- Recommended: Keep this section as shown below -->
Railway is a singular platform to deploy your infrastructure stack. Railway will host your infrastructure so you don't have to deal with configuration, while allowing you to vertically and horizontally scale it.

By deploying Uptime Kuma on Railway, you are one step closer to supporting a complete full-stack application with minimal burden. Host your servers, databases, AI agents, and more on Railway.
<!-- End recommended section -->
