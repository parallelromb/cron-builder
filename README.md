# Cron Builder

> **A visual cron expression builder with 6 export formats.** Free, open source, no signup, no tracking. Single HTML file.

🌐 Live at **[cron.parallelromb.dev](https://cron.parallelromb.dev)**

![Cron Builder screenshot](docs/screenshot.png)

## What it does

Build a cron expression three ways — **visual builder**, **22 presets**, or **paste & parse** — then export it to whatever scheduler you actually use:

| Export | What you get |
|---|---|
| **Crontab** | Standard `0 9 * * 1-5` line ready to paste into `crontab -e` |
| **Launchd** | Full macOS `.plist` with `<key>StartCalendarInterval</key>` |
| **Systemd** | `.timer` + `.service` unit files for Linux |
| **GitHub Actions** | `on: schedule:` workflow YAML (with the UTC reminder) |
| **Kubernetes CronJob** | `apiVersion: batch/v1` manifest with `timeZone` field |
| **node-cron** | JS snippet with the right `cron.schedule()` call |

Plus **timezone-aware next-run preview** — pick from 19 common timezones (UTC, browser local, all the `America/*`, `Europe/*`, `Asia/*`, `Australia/*`, `Pacific/Auckland`) and see the next 10 firings in that zone. This is the bit that catches people setting GitHub Actions schedules from non-UTC zones.

## Why another cron tool?

- **`crontab.guru`** — lovely description engine, but no visual builder, no presets, no exports beyond crontab itself.
- **Online-cron-job-builders** — usually a web form that emits one syntax. Most don't help if your target is launchd, systemd, or Kubernetes.

This tool's moat is the **6-format export** plus the **timezone preview**. If you're a polyglot dev who runs jobs across cron, GitHub Actions, and a Kubernetes cluster, this saves you `man 5 crontab` plus three doc-page tabs.

## Features

- 🧱 Visual field builder (minute/hour/day/month/weekday) with hover hints showing syntax for each field
- ✅ Live validity badge + human-readable description
- 🕐 Next-10-runs preview with timezone selector (browser local / UTC / 17 named zones)
- 🎯 22 presets (every minute → quarterly)
- 📋 6 export formats (crontab · launchd · systemd · GitHub Actions · Kubernetes · node-cron)
- 🔗 Shareable URL — `?expr=0+9+*+*+1-5` opens directly with that expression loaded
- 💾 Save to library + auto-history (all in `localStorage`)
- 🌓 Dark mode (auto from `prefers-color-scheme`, toggle persisted)
- 📱 Mobile-responsive
- ♿ Keyboard navigation throughout

## Run locally

```bash
git clone https://github.com/parallelromb/cron-builder.git
cd cron-builder
python3 -m http.server 8000
# open http://localhost:8000
```

Or just open `index.html` in your browser. It's a single self-contained HTML file with no build step.

## Deploy

It's static. Drop `index.html` anywhere:

- **Cloudflare Pages** — connect the repo, leave build empty, output dir `/`
- **GitHub Pages** — Settings → Pages → Deploy from branch `main`, root `/`
- **Vercel / Netlify** — same, no build config needed

## URL parameters

| Param | Example | What it does |
|---|---|---|
| `?expr=` | `?expr=0+9+*+*+1-5` | Pre-loads this expression on page open |

You can use `+` or `%20` for spaces.

## Privacy

Everything runs in your browser. No data leaves your machine — there's nothing to leave it for, since there's no backend. Your saved expressions and history live in your browser's `localStorage` for this domain only.

## Contributing

PRs and issues welcome. Some directions worth taking:

- More export formats (Quartz, AWS EventBridge, Airflow, BullMQ)
- Reverse parser — paste a launchd `.plist` and get the cron expression back
- Quartz-style 6-7 field expressions (with `?`, `L`, `W`, `#` operators)
- More timezones / IANA TZ search
- Translations

Big rewrites or framework migrations: please open an issue first.

## License

[MIT](LICENSE) — fork, embed, sell, whatever. Just keep the copyright line.

## About

Built by **Sri** ([parallelromb.dev](https://parallelromb.dev)) — solo hacker building [Lumen](https://parallelromb.dev), [Smara](https://smara.io), [MCP Doctor](https://mcpdoctor.ai), [Scoper](https://github.com/parallelromb/scoper), and a few other things.

Originally part of [`parallelromb/lumen-tools`](https://github.com/parallelromb/lumen-tools) — a marathon-night build of 58 self-contained browser tools — extracted and polished as a standalone product.

Pair-programmed with Claude (Anthropic).
