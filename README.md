# Live Denoising

A Jupyter notebook for experimenting with music-first denoising on live concert audio.

## Current Approach

This version uses traditional signal processing instead of a machine learning model:

- stereo-preserving audio loading with `soundfile`
- gentle spectral-gate noise reduction with `noisereduce`
- multiple denoising strengths for comparison
- light EQ enhancement
- spectrum visualization and audio playback inside the notebook

The current goal is to preserve the musical content first, then reduce audience and background noise where possible.

## Limitations

Live concert denoising is difficult with filters alone. Vocals, instruments, audience noise, room ambience, and reverb often overlap in the same frequency ranges, especially around 100-1000 Hz.

Because of that, this notebook can only perform conservative cleanup. Stronger settings may reduce more background noise, but they can also damage instrument tone, vocal continuity, and natural reverb tails.

For stronger separation between music and audience noise, a future ML-based source separation model would likely work better than traditional filtering.

## Usage

Place the input audio file in this folder as:

```text
concert.wav
```

Then open and run:

```text
Denoising.ipynb
```

The notebook generates local `.wav` outputs for listening and comparison. These audio files are ignored by git.

## Outputs

Depending on which cells are run, the notebook may generate:

```text
clean_music_first.wav
clean_music_medium.wav
clean_music_stronger.wav
enhanced_music_first.wav
enhanced_music_medium.wav
enhanced_music_stronger.wav
```

The `medium` version is currently the recommended starting point for a more audible but still relatively conservative result.

## Repository Notes

Generated audio files are excluded with `.gitignore` to keep the repository lightweight.

Before pushing changes, clear notebook outputs so `Denoising.ipynb` does not include embedded plots or audio players.

## Next Steps

Future work may explore ML-based source separation for better audience-noise reduction while preserving music quality.
