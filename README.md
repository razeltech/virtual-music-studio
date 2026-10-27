<div align="center">

![MAHATI — Virtual Music Studio](assets/banner.png)

# MAHATI — Virtual Music Studio
### Flagship Multi-Touch Polyphonic Audio Workstation & Instrument Rack

[![PWA Ready](https://img.shields.io/badge/PWA-Ready-10b981?style=flat-square)](#progressive-web-app-pwa--offline-operation)
[![Web Audio API](https://img.shields.io/badge/Audio-Procedural%20Web%20Audio-6366f1?style=flat-square)](#audio-synthesis-engines)
[![IndexedDB Storage](https://img.shields.io/badge/Storage-IndexedDB%20Sessions-f59e0b?style=flat-square)](#recording-engine--indexeddb-session-storage)
[![Zero Dependencies](https://img.shields.io/badge/Runtime%20Dependencies-0%20(Pure%20Vanilla)-06b6d4?style=flat-square)](#architecture--stack)
[![Live Demo](https://img.shields.io/badge/Live%20Demo-Launch%20Studio-38bdf8?style=flat-square)](https://razeltech.github.io/virtual-music-studio/)
[![Powered By](https://img.shields.io/badge/Powered%20By-Razel%20Tech-f43f5e?style=flat-square)](https://razeltech.github.io)

**Live Demo:** [https://razeltech.github.io/virtual-music-studio/](https://razeltech.github.io/virtual-music-studio/)  
**Repository:** [https://github.com/razeltech/virtual-music-studio](https://github.com/razeltech/virtual-music-studio)

*Powered by [Razel Tech](https://razeltech.github.io)*

</div>

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Audio Synthesis Engines](#audio-synthesis-engines)
  - [1. Polyphonic Grand Piano](#1-polyphonic-grand-piano)
  - [2. Physics Guitar & Fretboard](#2-physics-guitar--fretboard)
  - [3. Procedural Drum Kit Stage](#3-procedural-drum-kit-stage)
  - [4. Bowed Strings (Violin & Cello)](#4-bowed-strings-violin--cello)
  - [5. Concert Harp](#5-concert-harp)
  - [6. Sub-Bass & Marimba](#6-sub-bass--marimba)
  - [7. XY Synthesizer Pad](#7-xy-synthesizer-pad)
- [Interactive Song Academy & Trainer](#interactive-song-academy--trainer)
- [Recording Engine & IndexedDB Session Storage](#recording-engine--indexeddb-session-storage)
- [Master Bus, FX & 16-Step Sequencer](#master-bus-fx--16-step-sequencer)
- [Progressive Web App (PWA) & Offline Operation](#progressive-web-app-pwa--offline-operation)
- [Deep SEO & Structured Metadata](#deep-seo--structured-metadata)
- [System Architecture (BRAIN)](#system-architecture-brain)
- [Local Development & Deployment](#local-development--deployment)
- [License & Attribution](#license--attribution)

---

## Overview

**MAHATI** is a web-based multi-instrument music studio and polyphonic audio rack powered entirely by the native **HTML5 Web Audio API**. It operates without pre-recorded audio samples, WAV banks, or third-party audio libraries. Every waveform, transient impact, string vibration, and acoustic resonance is synthesized mathematically in real time with sub-millisecond response latency.

Designed from the ground up for multi-touch performance, MAHATI enables two-handed piano playing, continuous acoustic string bowing, physical guitar strumming, and simultaneous drum groove accompaniment within an integrated dark-mode studio workstation.

---

## Key Features

- **100% Procedural Synthesis:** Zero external audio file downloads. Works completely offline.
- **Sustained Long-Press Voice Lifecycle:** Grand piano voices sustain naturally while keys are held down, with release decay envelopes upon release.
- **Full Multi-Touch Polyphony:** Independent touch pointer tracking across unlimited concurrent contact points.
- **Interactive Multi-Instrument Song Academy:** Learn famous melodies with real-time target note highlighting that synchronizes across piano, guitar frets, bowed strings, harp, and bass bars. Disabled by default to preserve studio freedom, with instant one-click activation.
- **Master Audio Recorder with IndexedDB Storage:** Record full master output directly to browser IndexedDB, replay saved takes, and export tracks to audio files without server dependencies.
- **Stereo Delay FX & Dynamics Processing:** Studio compressor, stereo ping-pong dub delay send, and a 42-band real-time FFT spectrum visualizer.
- **16-Step Loop Sequencer:** Clock-synchronized groove engine with tempo control (60 to 180 BPM).
- **Progressive Web App (PWA):** Standalone installable application with automated landscape orientation management and offline Service Worker caching.

---

## Audio Synthesis Engines

| Instrument | Synthesizer Architecture | Sound Characteristics |
| :--- | :--- | :--- |
| **Grand Piano** | Dual detuned triangle/saw oscillators, low-pass filter, vibrato LFO | Acoustic resonance, sustained holding voices, chromatic octave shift |
| **Physics Guitar** | Fret frequency math, impulse pluck excitation, string vibration damping | Standard EADGBE tuning, 12 frets, visual spring vibration simulation |
| **Drum Kit Stage** | Procedural sine pitch drops, shaped white noise bursts, bandpass resonators | 8 pads: Kick, Snare, Hi-Hats, Toms, Clap, Rimshot, Cowbell |
| **Bowed Strings** | Dual sawtooth oscillators with continuous dynamic bandpass filtering | Continuous bowing physics for Violin and Cello |
| **Concert Harp** | Resonant bell bandpass filters, soft exponential pluck decay | 10 strings, modal presets (Major, Minor, Pentatonic, Blues, Dorian) |
| **Sub-Bass / Marimba** | Pure sine sub-octave oscillator with wooden mallet transient generator | 12 chromatic bars, dual mode (Sub-bass / Wooden Marimba) |
| **XY Synth Pad** | Dual detuned oscillators, continuous touch modulation | X: Cutoff frequency (80 Hz to 8 kHz), Y: Resonance ($Q$) and detune |

### 1. Polyphonic Grand Piano
Constructed with dual-oscillator detuning (+3 to +6 cents) and an acoustic low-pass filter (2800 Hz cutoff). Supports continuous sustained notes: holding down keys maintains the sound indefinitely, and releasing triggers an exponential release envelope to avoid click artifacts.

### 2. Physics Guitar & Fretboard
Six strings tuned to standard concert pitch (E2 82.41 Hz to E4 329.63 Hz). Fret positions calculate pitch according to the equal temperament law:
$$f = f_{0} \cdot 2^{n / 12}$$
Canvas animation renders damped harmonic spring physics on plucked strings.

### 3. Procedural Drum Kit Stage
Procedurally models acoustic drums:
- **Kick:** Fast exponential pitch drop from 145 Hz to 38 Hz in 80ms.
- **Snare:** 180 Hz body oscillator combined with shaped high-pass white noise.
- **Hi-Hats:** Metallic band-pass filtered noise bursts (0.04s closed, 0.32s open).
- **Toms & Percussion:** Tuned decaying resonators with harmonic balance.

### 4. Bowed Strings (Violin & Cello)
Models continuous friction bowing. Dragging a finger across the string canvas recalculates excitation point, string velocity, and dynamic brightness in real time. Switchable between Violin (G3, D4, A4, E5) and Cello (C2, G2, D3, A3).

### 5. Concert Harp
Ten resonant strings equipped with diatonic and modal scale matrices. Plucks produce acoustic bell decay with overtone diffusion.

### 6. Sub-Bass & Marimba
Features dual sonic profiles: deep foundation sub-bass with gentle saturation, or organic percussive marimba with quick harmonic transients.

### 7. XY Synthesizer Pad
Continuous two-dimensional parameter modulation pad. Moving a contact point simultaneously alters low-pass filter cutoff on the horizontal axis and resonance ($Q$-factor) on the vertical axis.

---

## Interactive Song Academy & Trainer

The studio includes an interactive song trainer that guides users through famous melodies step by step:

- **Repertoire:**
  - *Happy Birthday to You*
  - *Jingle Bells*
  - *Hedwig's Theme (Harry Potter)*
  - *Twinkle Twinkle Little Star*
  - *Beethoven's Ode to Joy*
- **Cross-Instrument Target Guidance:** Automatically computes and displays target positions on Grand Piano keys, Guitar frets (String and Fret notation), Bowed String positions, Harp strings, and Bass bars.
- **Default State:** Kept **disabled by default** to keep the studio clean for freeform performance. Once opened via the `SONGS` button, users can toggle between:
  - **Practice Mode:** Highlights the current target note and waits for the user to play it on any active instrument before advancing.
  - **Auto-Play Mode:** Automatically auditions each note across active studio instruments at the song's set tempo.

---

## Recording Engine & IndexedDB Session Storage

MAHATI features a local studio recording suite:

1. **Pure Master Audio Capture:** Taps directly into the post-compression, post-delay master audio stream using `MediaStreamAudioDestinationNode` and `MediaRecorder`.
2. **IndexedDB Session Persistence:** All recorded takes are stored locally in the browser's IndexedDB database (`MAHATI_Studio_DB`), ensuring recordings survive page refreshes and browser restarts without requiring cloud accounts or remote servers.
3. **Recordings Drawer:**
   - Review and play back previous takes with instantaneous audio replay.
   - Monitor take duration, timestamp, and index.
   - Download takes as standalone audio files (`.webm`, `.mp4`, `.ogg`).
   - Delete individual takes or purge all sessions with one click.

---

## Master Bus, FX & 16-Step Sequencer

```
[All Active Instruments]
         │
         ▼
    [Master Bus]
         │
         ├───► [Stereo Dub Delay] ──► [Feedback Loop (0.35)] ──┐
         │                                                     │
         ▼                                                     │
    [Dynamics Compressor] ◄────────────────────────────────────┘
         │
         ▼
    [Master Volume Gain]
         │
         ├───► [AnalyserNode] ──► 42-Band Real-Time Visualizer
         │
         ▼
    [Audio Hardware Output]
```

- **Dynamics Compressor:** -18 dB threshold, 4.5:1 ratio, 0.003s attack, 0.25s release. Prevents digital clipping during heavy polyphonic sessions.
- **Stereo Dub Delay:** 0.32s delay line with 35% feedback for atmospheric dub trails.
- **16-Step Loop Sequencer:** Programmable beat engine synchronizing drum grooves with live play.

---

## Progressive Web App (PWA) & Offline Operation

- **Standalone Mode:** Fully installable as an app on Windows, macOS, Android, and iOS.
- **Service Worker (`sw.js`):** Employs a stale-while-revalidate caching strategy to cache the complete application shell, icons, and CDN bundles for offline operation.
- **Orientation Lock:** Mobile devices running the installed application automatically lock to landscape orientation for optimal keyboard and fretboard ergonomics.

---

## Deep SEO & Structured Metadata

- Complete OpenGraph tags (`og:title`, `og:description`, `og:image`, `og:type`) optimized for rich previews across WhatsApp, Telegram, Twitter, Discord, and LinkedIn.
- Validated Schema.org `WebApplication` JSON-LD structured data.
- Search engine indexing directives via `robots.txt` and XML sitemap (`sitemap.xml`).
- Optimized social preview asset (`assets/og-preview.png`) compressed under 70 KB.

---

## System Architecture (BRAIN)

For engineering details, audio routing schematics, voice data structures, and instructions on adding new instruments or song sequences, consult the architecture documentation:

- [BRAIN.md](BRAIN.md) — Architectural blueprint and developer reference.

---

## Local Development & Deployment

MAHATI requires no compilation step. It can be served from any static file server or opened directly in a modern web browser.

### Option 1: Serve Locally via Node.js
```bash
# Serve with any lightweight static HTTP server
npx serve .
```

### Option 2: Serve via Python
```bash
# Python 3 built-in HTTP server
python -m http.server 8080
```

Open `http://localhost:8080` in Chrome, Edge, Firefox, or Safari.

---

## Topics & Discoverability Tags

```text
web-audio-api, virtual-instruments, music-studio, synthesizer, polyphonic-synth,
daw, pwa, drum-machine, guitar-simulator, piano-keyboard, audio-workstation,
interactive-tutorials, javascript-audio, indexeddb, html5-canvas, sound-synthesis,
offline-first, audio-effects, sequencer, music-production
```

---

## License & Ownership

**Copyright (c) 2026 [Razel Tech](https://razeltech.github.io). All rights reserved.**

This project is owned, developed, and maintained by **Razel Tech**.

Licensed under the **MIT License with Mandatory Author Attribution**:

> Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
>
> 1. The original copyright notice and this permission notice must be included in all copies or substantial portions of the Software.
> 2. **Mandatory Author Attribution:** Any public deployment, mirror, fork, modification, repackaging, or redistribution must visibly attribute the original author as **Razel Tech** and include an active hyperlink to **[https://razeltech.github.io](https://razeltech.github.io)** in the user interface, documentation, or repository landing page.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

