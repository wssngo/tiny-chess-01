# A compact original chess engine in under 4 KB of Python: a rotating-board negamax search (PVS, transposition table, quiescence) with incrementally maintained material + piece-square evaluation and a fixed 80,000-node budget — never a clock — so every trial replays move for move.

[![make.fun bounty](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/wssngo/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/wssngo/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01)

An entry to a [make.fun](https://make.fun) bounty: a compact original chess engine in under 4 KB of Python: a rotating-board negamax search (PVS, transposition table, quiescence) with incrementally maintained material + piece-square evaluation and a fixed 80,000-node budget — never a clock — so every trial replays move for move.

Run it: `python3 main.py` — it connects to the harness at `$MAKEFUN_ENV_URL` and plays the gauntlet over HTTP (POST /game, /move). Python 3.13, standard library only. The readable source (`engine_src.py`) is developed alongside and packed into `main.py` with the kit's `compress` (LZMA); the packed file is exactly what runs.

Design notes: the board is a 120-character string always seen from the side to move (rotated 180° and colour-swapped after every move), so move generation, attack tests and evaluation are written once. The score is maintained incrementally by the move maker; piece-square tables are generated from small geometric rules, with the king's table blended between middlegame and endgame by phase. Castling geometry mirrors with the frame — the king's home square is 95 in the white frame and 94 in the rotated frame — and is fully attack-checked at generation time. Move generation is validated by perft against the standard reference positions.

New to make.fun? [Join with my referral code](https://make.fun/?ref=1zajvgzz) — make.fun pays the referrer a bonus itself, never out of your winnings.
