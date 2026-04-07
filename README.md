# Stream (Render)

Same demo as [stream](https://github.com/rivet-dev/rivet/tree/main/examples/stream): real-time top-3 value tracker with persistent state, packaged with a [`render.yaml`](./render.yaml) Blueprint for [Render](https://render.com/) + [Rivet Cloud](https://rivet.dev/).

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https://github.com/ojusave/rivet-stream)

## Deploy on Render

Set **Root Directory** to `examples/stream-render` if deploying from the monorepo. Add **`RIVET_ENDPOINT`** (`sk_…`) and **`RIVET_PUBLIC_ENDPOINT`** (`pk_…`) from [dashboard.rivet.dev](https://dashboard.rivet.dev), then register the service HTTPS URL in Rivet. **`RIVET_ENVOY_VERSION`** is derived automatically from `RENDER_GIT_COMMIT`.

## Implementation

- **Actor** ([`src/actors.ts`](./src/actors.ts)): `streamProcessor` maintaining a sorted top-3 leaderboard with broadcast updates
- **Server** ([`src/server.ts`](./src/server.ts)): Hono app routing `/api/rivet/*` to the registry handler
- **Frontend** ([`frontend/App.tsx`](./frontend/App.tsx)): `useActor` hook with live stats and event-driven UI

**Reference:** [actions](https://rivet.dev/docs/actors/actions) · [state](https://rivet.dev/docs/actors/state) · [events](https://rivet.dev/docs/actors/events) · [Blueprint spec](https://render.com/docs/blueprint-spec)

MIT
