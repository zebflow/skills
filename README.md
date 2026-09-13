# Zebflow skills

The procedures an agent follows when it builds a Zebflow project: when to do
what, in what order, and what proves it worked. Each folder is one skill in
the [Agent Skills](https://agentskills.io) format — `SKILL.md` with `name`,
`description` (the trigger) and `license`.

These are the **blessed** skills. Every Zebflow project already serves them to
its agent over MCP (`skill_list`, `skill_read`, and as prompts), so an agent
connected to a project needs nothing from this repository. This repository is
for the agents that read skills from a folder instead — Claude Code, Codex,
Cursor, Copilot, Gemini CLI — and for anyone who wants to fork one.

## Install

```bash
npx skills add zebflow/skills                 # all of them, into the agent folders you use
npx skills add zebflow/skills --skill zebflow-basic
```

Claude Code plugin marketplace:

```
/plugin marketplace add zebflow/skills
/plugin install zebflow@zebflow-skills
```

## Skills

- [`procedural-assets`](./skills/procedural-assets/SKILL.md) — Building 2D and 3D assets in code, iteratively — an SVG icon, illustration or diagram; a Three.js mesh, prop, scene or character (zeb/threejs, or any engine); from a reference image or a brief. Use whenever you are about to draw or model something rather than download it — covers observe-then-spec, passes, render-and-compare, one decision per pass, budgets, and when to stop.
- [`zebflow-auth`](./skills/zebflow-auth/SKILL.md) — Login, sessions, roles and protected routes in a Zebflow project — JWT on triggers, cookies, registration, password hashing, OAuth (Google), public vs private claims, public vs private files. Use before building anything a visitor must be signed in for, or anything that must be hidden from one.
- [`zebflow-basic`](./skills/zebflow-basic/SKILL.md) — How to work in any Zebflow project over MCP. Use at the start of every session and whenever you are about to create, change or claim completion of anything in a project — orientation, the mutation rule, exact names, verification, memory.
- [`zebflow-data`](./skills/zebflow-data/SKILL.md) — Storing and querying data in a Zebflow project — Sekejap (the built-in database), SQLite, PostgreSQL by credential, tables, schema, migrations, seeds. Use before writing any SQL, creating a table, or adding a field; covers schema-first discovery, naming conventions, binds, and verifying with pipeline_run.
- [`zebflow-files-editor`](./skills/zebflow-files-editor/SKILL.md) — Uploads, images, files and rich text in a Zebflow project — FileRef, fs.save and fs.thumbnail, public vs private URLs, the zeb/ui editor and how its document is stored and rendered. Use before building an upload form, an image field, a media library, or any page with authored rich content.
- [`zebflow-hub`](./skills/zebflow-hub/SKILL.md) — Adding a package from the Zebflow Hub into a project, or publishing one — pipeline, template, folder and project bundles, node bundles, zeb/* libraries, skills. Use before any Add, install, clone or publish; covers the safety review, what lands where, drafts, zeb.lock, versions and presentation.
- [`zebflow-pipeline`](./skills/zebflow-pipeline/SKILL.md) — Building or changing a Zebflow pipeline — a route, an API endpoint, a page's data, a form's POST, a scheduled job, a webhook. Use before writing any DSL; covers the pair (pipeline + template) as the unit of done, flags, payload shape, register/activate, and the checks that prove a route works.
- [`zebflow-rwe`](./skills/zebflow-rwe/SKILL.md) — Writing or changing a TSX page, component or script in a Zebflow project — the RWE engine, zeb/react, imports, input, page config, hydration, Tailwind classes, and the compile-then-fetch-then-open loop. Use before any .tsx or .ts write.
- [`zebflow-ui`](./skills/zebflow-ui/SKILL.md) — Building a screen in a Zebflow project with the zeb/ui component set — buttons, forms, dialogs, tables, tabs, menus, toasts, the editor. Use when composing any UI, choosing between zeb/ui and a clone, applying theme roles, or laying out an admin shell, a list, a form or a detail page.
- [`zebflow-verify`](./skills/zebflow-verify/SKILL.md) — Proving that something in a Zebflow project works before reporting it done — fetching routes, reading bodies for RWE component error, invocations, and driving the page in a headless browser (console errors, clicks that must change state, forms, uploads). Use before every completion claim about a route or a page, and when a click "does nothing".

## How they relate to the platform

A skill points into the platform's help topics (`help(topic="…")` over MCP)
for the facts — node flags, routes, hooks — and never duplicates them. The
help is generated or guarded against the code; when a skill and the help
disagree, the help wins and the skill has a bug.

A project can add its own skills at `skills/<name>/SKILL.md` in its
repository, or clone one from the Zebflow Hub; a project skill with the same
name as a blessed one replaces it for that project.

Generated from `blessed/skills/` in the Zebflow repository at version
0.9.0 by `scripts/publish-skills.sh`. Changes go there.

## License

MIT — see [LICENSE](./LICENSE).
