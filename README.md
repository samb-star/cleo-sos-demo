# Cleo SOS — Demo

A working demo of the Cleo SOS concept. No server, no dependencies to install.

## Running it

1. Clone or download this repo
2. Open `index.html` in any browser
3. That's it

## What you're looking at

**Customer view** (default screen) — the weekly in-app quiz. Three tick-box questions, framed as a help raffle. Low friction, honest self-assessment. Users raise their hand.

**Internal dashboard** (click "View internal dashboard →") — the Cleo team view. Of everyone who entered the quiz, surfaces the member whose open banking data confirms they need help most.

## The data

150 dummy users are generated at runtime from a seeded algorithm — same data every load, no external calls. Each user has 730 days of realistic balance history across 5 financial archetypes:

- **Chronically distressed** (10 users) — trapped in a cycle, net negative each month
- **Moderately distressed** (20 users) — often negative, flat to declining trend
- **Occasional struggle** (40 users) — dips negative, slowly recovering
- **Mostly healthy** (50 users) — rarely negative
- **Comfortable** (30 users) — consistently positive, growing

Quiz entrants skew toward distressed archetypes (they're more likely to self-select in).

## Scoring (100pts)

| Signal | Points | What it catches |
|---|---|---|
| 2-year avg balance | 15 | Chronic baseline — this is their life |
| 180-day avg | 15 | Medium-term trajectory |
| 90-day avg | 20 | Recent quarter |
| 30-day avg | 20 | This month |
| Current balance | 10 | Right now |
| Cross-window deterioration | 20 | Are all windows getting worse together? |

The hero is the person who bottoms out across all five — not someone having a bad month, but someone whose two-year trend tells a story of sustained distress.

## Help amount logic

```
Clear negative  =  ABS(current balance)
½-month buffer  =  estimated monthly spend × 0.5
Recommended     =  clear negative + buffer
```

Monthly spend is estimated from the user's own open banking pattern (average negative daily delta over 90 days).

## The bigger idea

After 6 months of weekly draws, the aggregate story becomes a marketing asset: *"We've helped X people by paying their balances — chosen by data, not luck."* This replaces Money IQ's gamified prize mechanic with something more honest and more Cleo.
