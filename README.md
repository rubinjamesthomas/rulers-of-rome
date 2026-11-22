# Rulers of Rome

A local pass-and-play Roman mythology card game for 2–4 players, built with React, TypeScript and Vite.

## Play locally

1. Install Node.js 20.19+ or 22.12+.
2. Run `npm install` in this folder.
3. Run `npm run dev`.
4. Open the local address printed in the terminal.

## Publish on GitHub Pages

1. Create a new GitHub repository (for example `rulers-of-rome`).
2. Push these files to its `main` branch.
3. In GitHub, open **Settings → Pages → Build and deployment** and choose **GitHub Actions** as the source.
4. The included workflow builds and deploys automatically. The site will be available at `https://YOUR_USERNAME.github.io/rulers-of-rome/` (replace with your actual names).

## Rules implemented

- Deck: 4 each of point cards 1–6, 5 each of Neptune/Vulcan/Terra/Ventorum, and 4 Jupiter cards (48 total).
- Deal five cards per player; draw one and play one each turn.
- Played point cards add to the player's public score; cards remaining in hand do not count.
- Neptune skips the next player. Vulcan removes up to 2 points from a chosen player. Jupiter steals up to 3 points. Terra can be spent immediately to block Vulcan or Jupiter. Ventorum swaps two selected cards from your hand with two chosen face-down cards from another player's hand.
- Once the final deck card is drawn, that player finishes their turn and highest score wins. Ties are shared.
- House-rule assumptions: Terra cannot be played proactively, Neptune cannot be blocked (it targets the next player's turn automatically), and Ventorum cannot be blocked. A hand consisting entirely of Terra cards may pass. Players with fewer than two cards cannot be Ventorum swap targets successfully.

## Privacy limitation

This is local pass-and-play: the device must be passed discreetly. The opponent's hand is displayed only as card backs during a Ventorum choice. The current implementation does not hide the name of the attacker during a Terra reaction, and there is no networked multiplayer or persistent game save.

## Deferred God-card scoring (v1.1)

Vulcan and Jupiter effects are queued when played, then applied at the end of the game after the final turn. Vulcan deducts exactly 2 points from its target; Jupiter transfers exactly 3 points from its target to the attacker. This guarantees the full value even when the target has fewer points at the time of play. Final scores can be negative. The scoreboard shows played points and pending adjustments separately until settlement. Terra prevents an attack from being queued.
