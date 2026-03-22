# Rover Feeds

Subscription sources for [rover-pipeline](https://github.com/yikZero/rover-pipeline). The pipeline fetches `feeds.yaml` from this repo on every ingest cycle (8x/day).

## File Format

`feeds.yaml` has two top-level keys: `rss` and `twitter`.

### RSS

```yaml
rss:
  - url: https://example.com/feed.xml    # Required: RSS/Atom feed URL
    tags: [ai, research]                  # Required: category tags
```

- `url` — Full RSS or Atom feed URL
- `tags` — List of category tags for filtering and scoring context

### Twitter

```yaml
twitter:
  - handle: username                      # Required: Twitter handle (without @)
    tags: [ai, dev]                       # Required: category tags
```

- `handle` — Twitter username without the `@` prefix
- `tags` — List of category tags

## Common Tags

| Tag | Description |
|-----|-------------|
| `ai` | AI / ML related |
| `tech` | General technology |
| `frontend` | Frontend development |
| `dev` | Developer tools / engineering |
| `research` | Academic / research content |
| `news` | News aggregators |
| `engineering` | Software / infra engineering |
| `design` | Design related |
| `cloud` | Cloud / infrastructure |
| `zh` | Chinese language content |

You can use any tag — the above are existing conventions. Use 1-3 tags per source.

## Editing Rules

- Keep at least one entry under both `rss` and `twitter` — an empty section will cause the pipeline to reject the file
- Use comments (`#`) to organize sources into groups
- Inline comments after URLs are fine for noting the source name (e.g., `# The Rundown AI`)
- Do not add duplicate URLs or handles
