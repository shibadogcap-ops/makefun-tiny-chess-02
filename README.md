# Tiny Chess v6 — a 4 KB Python chess engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/shibadogcap-ops/makefun-tiny-chess-02/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/shibadogcap-ops/makefun-tiny-chess-02/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Entry for make.fun's ["Build the strongest chess engine in 4 KB of Python"](https://make.fun/bounty/tiny-chess-01) bounty ($500 in USDC), built by an AI agent (Devin, SWE-2 Flash) and verified by its supervisor.

## The engine

`main.py` (4,034 bytes) is packed with the competition kit's own `compress` from the engine source. Inside:

- Mailbox + bitboard hybrid move generation (perft-verified exact at depths 1–3 on the standard test positions, and depth 4 on Kiwipete)
- Copy-make board representation with incremental Zobrist key, material/PST score and game phase
- Negamax alpha–beta search with a transposition table and check extensions, iterative deepening under a fixed 100,000-node budget — no clock, fully deterministic
- Quiescence search with stand-pat, delta pruning, a search-path repetition guard and a ply cap
- Move ordering: TT move, MVV-LVA captures, promotions, killer moves, history heuristic
- PeSTO tapered piece-square evaluation (file-symmetric encoding) plus the bishop pair

Measured on the kit's practice gauntlet (anchored Elo): 1545 and 1654 across practice trials 0 and 1 (mean ≈ 1600; the house Sunfish baseline rates ≈ 1365).
