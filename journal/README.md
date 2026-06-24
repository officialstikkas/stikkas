# journal-jekyll/ — Stikkas Journal Deploy Backup

Source of truth backup for the Jekyll journal deploy built 2026-06-02.
The active deploy clone lives at `/tmp/stikkas` (volatile per workspace docs).
This backup lives inside the workspace so the nightly GitHub backup catches it.

## Files (mapping back to live site paths)

- `root-index.md` → repo root `index.md`
- `journal-index.md` → repo `journal/index.md`
- `print-wedding-planner-at-home.md` → repo `journal/print-wedding-planner-at-home.md`
- `how-to-use-an-adhd-planner.md` → repo `journal/how-to-use-an-adhd-planner.md`
- `printable-vs-app-planners.md` → repo `journal/printable-vs-app-planners.md`
- `mini-lab-notebook.md` → repo `journal/mini-lab-notebook.md`
- `_config.yml` → repo `_config.yml`
- `head_custom.html` → repo `_includes/head_custom.html`

## Restore flow if /tmp/stikkas is gone

```bash
cd /tmp && rm -rf stikkas && git clone https://github.com/officialstikkas/stikkas.git
cd stikkas
mkdir -p _includes journal
cp ~/.openclaw/workspace/stikkas-site/journal-jekyll/root-index.md index.md
cp ~/.openclaw/workspace/stikkas-site/journal-jekyll/journal-index.md journal/index.md
cp ~/.openclaw/workspace/stikkas-site/journal-jekyll/print-wedding-planner-at-home.md journal/
cp ~/.openclaw/workspace/stikkas-site/journal-jekyll/how-to-use-an-adhd-planner.md journal/
cp ~/.openclaw/workspace/stikkas-site/journal-jekyll/printable-vs-app-planners.md journal/
cp ~/.openclaw/workspace/stikkas-site/journal-jekyll/mini-lab-notebook.md journal/
cp ~/.openclaw/workspace/stikkas-site/journal-jekyll/_config.yml .
cp ~/.openclaw/workspace/stikkas-site/journal-jekyll/head_custom.html _includes/
git add -A && git commit -m "Add journal: 4 SEO posts + landing page"
git push origin main
```

See `PUBLISH-NOW-JOURNAL.md` in workspace root for full publish context.
