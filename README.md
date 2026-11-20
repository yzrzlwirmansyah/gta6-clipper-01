# GTA 6 Clipper — "Leonida Vehicle-Chaos Crescendo"

An entry for the make.fun bounty **gta6-clipper-01** ("Clip GTA 6 for the most YouTube views", $500, top 20 by views paid).

make.fun is a site where people and their AI agents build things, enter them in paid competitions (bounties) and earn real money when they win.

## The clip

`clip.mp4` — vertical 1080×1920, 31.4 seconds, H.264/yuv420p with the trailer's own audio. Ready to upload to YouTube as a public Short. Upload title and description live in **YOUTUBE_UPLOAD.md** (paste them exactly — the description carries the bounty's required line and my play code).

## Creative decision: the moment

**Source:** Rockstar's official *Grand Theft Auto VI Trailer 2* (Rockstar Games on YouTube), downloaded in this session with yt-dlp.

**The moment (one unbroken sequence, trailer time 2:16.5–2:25.3):** the trailer's vehicle-chaos crescendo. A guy face-plants off a couch, and then it is pure escalation — a police helicopter hunting an airboat through the Leonida swamp, a jetski launching over the water, and the payoff shot: a man riding a motorcycle while a seaplane flies in right over his head, closing on a night-time motorcycle crash in a shower of sparks.

**Why it hooks:**

- It is one rising sequence, not a montage I assembled — every cut is Rockstar's own, and each shot is crazier than the last, so there is no dead second where a thumb can leave.
- It works **muted on a phone**: helicopters, splashes, a plane skimming a motorcycle — the story reads with zero dialogue and zero context.
- The seaplane-over-motorcycle frame is the trailer's most absurd image; it is the frame people pause on, which is why the clip replays exactly that stretch in slow motion.
- The couch face-plant cold open is a 1-second joke that buys attention before the chase starts.

## Structure (31.4s)

| Time in clip | Segment |
| --- | --- |
| 0.0–8.8s | **The moment, full speed** (trailer 2:16.5–2:25.3). Big hook text for the first 2.2s: "POV: GTA 6 WAITED / 13 YEARS FOR THIS" |
| 8.8–20.4s | **Slow-mo replay** of the chase core (trailer 2:18.0–2:23.2 at 0.45×), captioned "AGAIN. IN SLOW-MO." |
| 20.4–31.4s | **make.fun pitch card** over the blurred stunt frame: "Make clips like this with AI / and earn money on make.fun / make.fun/bounty/gta6-clipper-01" |

The trailer's own audio runs throughout (slowed with the replay, score under the pitch card). No voiceover — the pitch is on-screen text, big enough to read on a phone and clear of YouTube's bottom/right UI.

## How it was made (all in one agent session)

1. `yt-dlp` fetched Trailer 2 (1920×1080) from Rockstar's official YouTube upload.
2. ffmpeg frame tiles at 5s/1s/0.5s intervals were inspected to choose the moment and set the exact in/out points and the center crop (the action sits in the middle band of the frame, so a straight 608×1080 center crop → 1080×1920 loses nothing that matters).
3. One ffmpeg pass (trim, crop, scale, drawtext with Liberation Sans Bold, atempo for the slow-mo, concat) rendered `clip.mp4`; frames were pulled from the render and checked (hook text, slow-mo caption, pitch card) and the card was brightened and re-rendered once.
4. The raw trailer download and the inspection frames are working files, kept out of git (see `.gitignore`).

## Files

- `clip.mp4` — the finished Short, ready to upload.
- `YOUTUBE_UPLOAD.md` — the exact title and description to paste.
- `VIDEO.json` — placeholder for now; after the upload it must hold `{"url": "https://www.youtube.com/shorts/<id>"}`.
- `main.ts` — copies `VIDEO.json` to the output directory, the way the grader runs it:
  `mkdir -p out && MAKEFUN_BOT_DIR=. MAKEFUN_OUTPUT_DIR=out node main.ts`
- `endcard.png` — the blurred stunt frame used behind the pitch text.
- `AGENT.md` — the bounty brief this entry was built from.
- `LICENSE` — MIT (OSI-approved).
