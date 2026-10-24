# XXFAST

The home of everything `xxfast` the brand needs, that isn't a single project. One place for the automation every other project leans on.

This repo is public and doubles as the GitHub profile README. Site, store tooling and domain list are all public by nature, so that's fine. Anything that isn't (account emails, billing, recovery details, renewal dates) doesn't go here at all, not even in a note. Password manager, not markdown.

Global prefs (voice, git rules, no em-dashes, `gh` accounts) come from `~/.claude/CLAUDE.md`. Don't repeat them here. This file is only what's specific to this repo.

## What lives here

| Area | What |
|---|---|
| `site/` | Personal portfolio website. Source, content, deploy. |
| `stores/` | App Store Connect and Play Console. Listings, screenshots, release and review automation, shared metadata every app reuses. |
| `domains/` | Domain inventory, DNS, renewals, certs. |

None of these exist yet. Add a folder when there's something to put in it, not before. Each folder gets its own `AGENTS.md` once it has rules worth stating.

## Principles

- Simplest thing that works. A shell script beats a framework. A file beats a database.
- Everything is reproducible from this repo plus secrets. If a step needs a click in a dashboard, write it down in the relevant folder's `AGENTS.md` until it's automated.
- One source of truth per fact. App names, bundle ids, domains, brand colours live here once and get pulled into the projects, never copied.
- Other projects consume this repo. Don't make it depend on them.

## Secrets

- Never committed. Not in files, not in commit messages, not in chat. The repo is public, so a leak is scraped within minutes.
- Local: `.env` (gitignored). CI: the runner's secret store.
- Ask for a secret with `request_secret` when in T3 Code. Otherwise tell me what's needed and stop.
- Store credentials (ASC API keys, Play service accounts), registrar tokens and hosting tokens are the blast radius of this repo. Treat any action that uses them as outward-facing: show me what will run before running it.

## Outward-facing actions

Deploying the site, submitting a build, changing DNS, moving a domain, any billing. Confirm first every time. Dry-run where the tool has one.

## Cross-project work

Projects live under `Developer/XXFAST`. It's fine to read them to pull a bundle id or check a version. Don't edit them from here unless asked.
