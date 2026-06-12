---
title: "Sound only coming from headphone jack"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by jamil_1 on 2009-10-30
Hi i have installed ubuntu 9.10 today. Everything is working fine except sound. I can hear sound in my headphone but no sound comes from the speakers.
I have compaq persario cq61 
lspci -v spits this out about the sound card:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 306a
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d7000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by Brandon Williams on 2009-10-30
Open a terminal and run the following:
```
amixer scontrols
```

Does it list, among other things, "Simple mixer control 'Speaker'"?

If it does, then run:
```
amixer sget Speaker
```

Does it indicate that Playback is "[on]" or "[off]"?

If it says "[off]", then run:
```
amixer sset Speaker on
```

---

### Post by jamil_1 on 2009-10-30
jamil@jamil-laptop:~$ amixer scontrols
Simple mixer control 'Master',0
Simple mixer control 'Headphone',0
Simple mixer control 'PCM',0
Simple mixer control 'Mic Jack Mode',0
Simple mixer control 'IEC958',0
Simple mixer control 'Capture',0
Simple mixer control 'Capture',1
Simple mixer control 'DAC0',0
Simple mixer control 'DAC1',0
Simple mixer control 'Digital Input Source',0
Simple mixer control 'Digital Input Source',1
Simple mixer control 'Import0 Mux',0
Simple mixer control 'Import1 Mux',0
Simple mixer control 'Input Source',0
Simple mixer control 'Input Source',1
Simple mixer control 'Mux',0
Simple mixer control 'Mux',1
Simple mixer control 'PC Beep',0
Simple mixer control 'Speaker',0


and 


jamil@jamil-laptop:~$ amixer sget Speaker
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]

---

### Post by Brandon Williams on 2009-10-30
Google pointed me at [this document](https://help.ubuntu.com/community/HdaIntelSoundHowto).

---

### Post by jamil_1 on 2009-10-30
finally got it working:D 
I had to insert a line at the end of alsa-base.conf

options snd-hda-intel model=hp-hdx

---

