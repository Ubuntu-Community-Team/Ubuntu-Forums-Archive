---
title: "Audacity not recording"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by blues2use on 2009-09-28
Once again, Audacity has decided to not record. I don't know if a recent update caused this problem or not but I had been recording successfully for a couple of months. As of today, no recording capability using versions 1.3.7 and 1.3.9. 

I have read and applied a bunch of "Audacity/sound system related fixes" and hacked around with Pulse Audio, Esound, OSS, Alsa, etc. from the forums, all to no avail. I've reinstalled linux-sound-base and the ubuntu-desktop several times. Streaming videos, Internet audio/video, CD's, etc all work fine as does recording with Sound Recorder. I use Audacity quite a lot for recording/editing and, when it works in ubuntu, it's great! When it doesn't work, not so great...

Does someone have a "step-by-step" procedure to unscrew Audacity so that it will record like it used to or to set it up to record without having to hack the jaunty sound system every time it decides to take a hike? (hate to say it, but it has always worked just fine on XP)...

Here's the 411 on my sound card: 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 2808
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Your suggestions are most appreciated...

**SOLVED**

Finally, somehow got **ALSA plug-in [audacity]: ALSA Capture** to show up on the **pavucontrol** and by selecting **"Move Stream"** _from_ **"HDA Intel - ALC260 Analog"** _to_ **"Monitor of HDA Intel - ALC260"** the VU meters showed signal in Audacity and I can record again.

My system sound preferences are:

Sound Events: PulseAudio Sound Server

Music and Movies: PulseAudio Sound Server

Audio Conferencing:

Sound Playback: PulseAudio Sound Server
Sound Capture: HDA Intel ALC260 Analog (OSS)

Default Mixer Tracks:

Device: HDA Intel (Alsa mixer)

All devices are selected

Hope this helps someone else...

---

