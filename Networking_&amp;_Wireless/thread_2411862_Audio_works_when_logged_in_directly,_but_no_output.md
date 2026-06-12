---
title: "Audio works when logged in directly, but no output devices when connecting w/ RDC"
date: 2019-02-04
forum: Networking &amp; Wireless
---

### Post by jasonjason2 on 2019-02-04
good evening,

i am running Samba 4.7.6-Ubuntu on 18.04LTS.

my audio card works fine when logged directly onto my machine. 

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DSX [Xonar DSX], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DSX [Xonar DSX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci | grep -i audio
02:00.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM]

$ sudo alsa force-reload
[sudo] password for jason: 
Unloading ALSA sound driver modules: snd-hrtimer snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-virtuoso snd-oxygen-lib snd-mpu401-uart snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hrtimer snd-hda-codec-hdmi snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq snd-seq-device snd-timer).
Loading ALSA sound driver modules: snd-hrtimer snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-virtuoso snd-oxygen-lib snd-mpu401-uart snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.

$ pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
```

however, if i connect to the machine via RDC, **without FIRST logging in directly**, i have no audio devices available in my sound mixer. 

it feels like a permissions issue, where RDC connections don't have  rights to control audio devices unless those audio devices have already  been used by local user?

i'm stumped!

---

