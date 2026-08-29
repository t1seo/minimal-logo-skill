# IP as Logo

`ip-as-logo` is a compact Agent Skill for generating extremely simple, cute, company-ready IP marks across five subject classes: creatures, objects, letterforms and numerals, geometric marks, and symbols. It prioritizes lovable character appeal, bold rounded silhouettes, strict complexity limits, a dominant lower-corner composition, and a solid named background color.

It follows the open Agent Skills format and is designed to work with any compatible AI agent, rather than being tied to a specific agent product.

You can also browse the free [IP as Logo Skill website](https://ipaslogo.com), a searchable library backed by Cloudflare R2 and Supabase.

![IP as Logo showcase](assets/ip-as-logo-wall.webp)

**Don't have Codex, Doubao, Coze, or Workbuddy?** [Visit our website](https://ipaslogo.com) to download ready-made logos for free. Every logo is free for commercial use.

## What it guides

- One dominant silhouette built from roughly 4–7 large basic shapes
- Three semantic colors by default: two IP base colors plus one background color
- Three proposed directions followed by six independently generated candidates after user approval
- Five subject classes sharing one visual system: creatures, objects, letterforms and numerals, geometric marks, and symbols, with a curated catalog in `references/subject-catalog.md`
- Familiar animals as the anchor for open-ended mascot requests, with product-relevant objects, brand-initial letterforms, geometric marks, and symbols as first-class directions whenever they map to the product
- Context-aware, clearly separated subject colors and gently muted, slightly lower-saturation backgrounds with barely-there neo-skeuomorphic depth, described without percentages or prescribed gradient and shading formulas
- Thick, rounded forms without sharp or fragile details
- A large, visually dominant IP emerging flexibly from the lower-left or lower-right, without prescribing a fixed crop
- A balanced default six-image split: three lower-left and three lower-right
- Extreme simplification, cute baby-like appeal, and removal of nonessential lines and details
- One named solid background color filling the square, without image-mode language in the generation prompt
- Image-only generation prompts that never reveal logo, brand-mark, app-icon, or icon-asset use
- One-pass batch generation that preserves and delivers every returned image without filtering or automatic retries

## Subject classes

Every class shares the same canvas, three-semantic-color system, corner-emergence composition, and cute rounded shape language. `references/subject-catalog.md` lists roughly 415 proven subjects across the five classes, organized by product domain.

| Class | Examples | Default face |
| --- | --- | --- |
| Creatures | fox, owl, octopus, ghost, robot | Always personified |
| Objects | rocket, open book, coffee mug, camera, key | Tiny face; faceless on request |
| Letterforms & numerals | `A–Z`, `0–9`, brand initial first | Tiny face; faceless on request |
| Geometric marks | circle, squircle, hexagon, blob, crescent | Tiny face; faceless on request |
| Symbols | heart, star, lightning bolt, shield, speech bubble | Tiny face; faceless on request |

## Install

Install the complete skill with the Agent Skills CLI:

```bash
npx skills@latest add t1seo/minimal-logo-skill
```

The installer detects the repository's root `SKILL.md`, lets you choose a supported coding agent, and installs the complete `ip-as-logo` directory, including its supporting assets. Use `--global` for a personal installation available across projects:

```bash
npx skills@latest add t1seo/minimal-logo-skill --global
```

This repository is a fork of [s1dashu/ip-as-logo-skill](https://github.com/s1dashu/ip-as-logo-skill) that expands the subject space from animal-first mascots to the five subject classes above.

## Agent compatibility

Supported agents include **Codex, Coze, Doubao, YouMind, Manus, Gemini Apps, and Replit Agent**. The agent must have a top-tier image model: preferably GPT Image 2, or Seedance 5.0 Pro, Nano Banana Pro (Gemini Image Pro), or Nano Banana 2 (Gemini Image Flash). If none is available, enable a suitable tool or provide its API key. The skill never falls back to SVG; another image model may be used only with explicit user consent, with no guarantee of equivalent quality.

## Use

Ask your AI agent for an IP mascot image, for example:

```text
Create a very simple, cute rounded ghost IP character on a solid deep navy background.
```

Objects, letterforms, geometric shapes, and symbols work the same way:

```text
Create a very simple, cute rounded rocket IP character on a solid dusk purple background.
Create a cute rounded letter B character for our brand initial on a solid sage green background.
Create a cute rounded hexagon character on a solid warm sand background.
Create a faceless heart mark on a solid soft coral background.
```

The skill does not ask for a color-mode choice by default. Every default candidate uses three semantic colors: two IP base colors plus one background color. It no longer reserves any fraction of the candidate set for two-color images. A two-color image is generated only when the user explicitly requests it, and then uses background-colored negative space for facial marks rather than introducing a third color.

When the user already names an IP subject — an animal, an object like a rocket or coffee mug, a letter, a digit, a geometric shape, or a symbol — the skill proposes three controlled design treatments of that subject. When the subject is open, it proposes three genuinely different directions and draws them from more than one subject class when the product context supports it: typically one familiar animal mascot, one product-relevant object or symbol, and one brand-initial letterform or geometric mark. Every direction is tied to a product attribute or brand promise, never chosen to manufacture novelty.

Large batches create variety through species or subject choice, proportions, expression, lower-left versus lower-right emergence, crop, silhouette, and secondary color organization. Objects, letterforms, geometric marks, and symbols follow the same cute rounded visual system as animal mascots: personified with a tiny face by default, faceless only on explicit request. The curated subject space in `references/subject-catalog.md` spans roughly 415 subjects across the five classes.

If the skill runs inside a product repository, it inspects relevant read-only context before asking questions. If product context is insufficient, it asks one consolidated round of background questions. Once context is sufficient, it always presents three concise directions and proposes generating six independent images. It proceeds after the user agrees, or immediately when the user has already explicitly authorized six outputs.

When the user accepts all three directions, the default batch contains two variants per direction: `A1`, `A2`, `B1`, `B2`, `C1`, and `C2`. The first variant of each direction emerges from the lower-left and the second from the lower-right. When the user selects one direction, odd-numbered variants use the lower-left and even-numbered variants use the lower-right. This guarantees a three-left, three-right default split. If the user rejects the proposed quantity or distribution, their replacement instructions take precedence.

Every default candidate emerges from the lower-left or lower-right rather than the center or bottom-center and fills roughly 85–95% of the square so the IP remains visually dominant. Bottom or side cropping may strengthen the corner emergence, but the Skill does not prescribe exact edge contact or a fixed crop.

Compatible agents may generate the six candidates in parallel with subagents up to the runtime's available concurrency, using additional waves when needed. The skill checks for a supported top-tier image model before generation and asks the user to enable one or provide its API key when necessary. Every result is a separate full-resolution square asset, never a six-image contact sheet.

When the user does not supply a palette, the skill gently lowers background saturation so the result feels a little more muted and controlled while remaining clearly chromatic, clean, and intentional rather than vivid, gray, or muddy. It keeps the normal design to exactly three semantic colors: two IP base colors plus the background. The generation prompt names the intended solid background color directly and avoids terms such as `opaque`, `alpha`, or `transparency` that may distract the image model from the desired visual result.

Although the project is named `ip-as-logo`, the prompt sent to the image generator describes only the requested square character image. It never calls the result a logo, brand mark, app icon, or icon asset, and it does not prepend use-case metadata that reveals those purposes.

Generation is intentionally treated as a creative draw. Each requested candidate is generated once and delivered as returned. The skill does not inspect transparency, block outputs, classify candidates as compliant or non-compliant, or automatically retry results because of their background, colors, composition, gradients, shading, or dimensionality. Users can explicitly request another draw or a refinement after reviewing the batch.

## Repository structure

```text
SKILL.md
references/subject-catalog.md
assets/ip-as-logo-wall.webp
README.md
LICENSE
```

The skill consists of a single instruction document plus one curated subject catalog that the agent consults when proposing directions. The repository also includes the showcase image above, but no scripts, style references, or generation dependencies.

## Model behavior

Image-generation models are stochastic and may interpret individual constraints differently. The skill preserves and returns every result without validation gates, transparency checks, automatic rejection, automatic retry, or silent repair.

## License

MIT
