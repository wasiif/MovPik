# Project: MovPik
A mood-based movie/TV picker. The user drags an orb on a mood canvas, sets a few context pills, and gets ONE great pick plus 2 backups. Not a list of 50.

## Stack (do not deviate)
- SvelteKit, Svelte 5 (runes: $state, $derived, $effect, $props), TypeScript strict
- Plain CSS with CSS variables. No Tailwind, no UI kit, no animation library.
- Motion: Svelte's built-in `spring`/`tweened`/transitions only
- Data: TMDB API, called ONLY from SvelteKit server routes. API key via `$env/static/private`. Never expose it to the client.

## Hard rules
- NO database, NO localStorage/sessionStorage/IndexedDB, NO cookies for state, NO accounts.
- All state is in-memory for the current visit. Refresh = reset. That is intentional.
- Server routes are stateless. The client sends its "seen/skipped" ID list with each request.
- Small files, small functions, no clever abstractions. Comments explain WHY, not WHAT.
- Every interactive element must be keyboard accessible. Respect `prefers-reduced-motion`.

## Design rules (anti AI-slop)
- NO purple-to-blue gradients, NO glassmorphism, NO neon glow, NO sparkle icons, NO emoji as UI icons.
- Hand-picked palette per mood zone (defined in tokens.css). Do not invent new colors ad hoc.
- Editorial typography: a serif for titles, one clean sans for UI. Real size hierarchy.
- Real posters and backdrops do the visual work. Decoration stays minimal.
- Motion has ONE idea: the orb and the reveal. No scroll-fade-in on everything.

## Voice (this matters)
Dry, short, specific, a little self-aware. Like a friend with good taste who is mildly tired.
- Good: "96 minutes. Quiet, funny, nothing blows up."
- Bad: "Embark on an unforgettable cinematic journey!"
- No exclamation marks. No "discover", "curated", "unleash", "elevate", "seamless".
- Errors, loading and empty states each get a human-written line with a bit of humor.
- All user-facing copy lives in `src/lib/copy.ts`. Never hardcode strings in components.
