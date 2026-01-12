# Human

## Development

```bash
docker-compose -f docker-compose.dev.yaml up
```

- **Backend**: Python code mounted at `/app/backend`, reloads on changes via uvicorn --reload
- **[Frontend](http://localhost:3000/)**: Javascript code mounted at, runs Vite dev server with hot reload

## Production

```bash
docker-compose up
```

## Syncing upstream changes

```bash
git fetch upstream
git checkout main
git merge upstream/main --ff-only
git push origin main
git checkout mb-spike
git rebase main
```

## Changelog

### Dec 31, 2025
Initial setup with upstream pre-built image:
```bash
docker run -d -p 3000:8080 -e OPENAI_API_KEY= -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

### Jan 9, 2026
- Forked to `superworkers/open-webui`
- Limited OpenAI models to `gpt-5.2` via `OPENAI_API_CONFIGS`

### Jan 12, 2026
- Added development workflow with code mounting and hot reload
- Set up upstream remote for syncing with `open-webui/open-webui`
