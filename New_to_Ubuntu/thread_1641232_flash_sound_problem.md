---
title: "flash sound problem"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by trikster_x on 2010-12-08
I do not get any sound output from anything flash based, like youtube or pandora.  I can play sound from dvd or other a/v files in totem, but I get nothing from web based flash.  I have checked alsamixer, and my levels are fine.  All my settings are okay in my preferences.  I installed flash-player from the adobe site using the .deb package, but still no sound.  Everything works fine on my other computers, which leads me to believe there is a problem between flash and my sound-card drivers.  I really hope this isn't the case, since I just got this sound card because of Ubuntu not playing nice with the alsa drivers for my on-board controller.

This is the card I am currently using:

```
02:09.0 Multimedia audio controller: Trident Microsystems 4DWave DX (rev 02)
	Subsystem: Trident Microsystems 4DWave DX
	Flags: bus master, medium devsel, latency 32, IRQ 19
	I/O ports at a000 [size=256]
	Memory at ea0a2000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Trident4DWaveAudio
	Kernel modules: snd-trident

```

If I need to provide any other info, just let me know what and how to get it.  Thanks.

---

### Post by Autodave on 2010-12-08
> **trikster_x said:**
> I do not get any sound output from anything flash based, like youtube or pandora.  I can play sound from dvd or other a/v files in totem, but I get nothing from web based flash.  I have checked alsamixer, and my levels are fine.  All my settings are okay in my preferences.  I installed flash-player from the adobe site using the .deb package, but still no sound.  Everything works fine on my other computers, which leads me to believe there is a problem between flash and my sound-card drivers.  I really hope this isn't the case, since I just got this sound card because of Ubuntu not playing nice with the alsa drivers for my on-board controller.

This is the card I am currently using:

```
02:09.0 Multimedia audio controller: Trident Microsystems 4DWave DX (rev 02)
    Subsystem: Trident Microsystems 4DWave DX
    Flags: bus master, medium devsel, latency 32, IRQ 19
    I/O ports at a000 [size=256]
    Memory at ea0a2000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Trident4DWaveAudio
    Kernel modules: snd-trident

```If I need to provide any other info, just let me know what and how to get it.  Thanks.

Have you installed "ubuntu-restricted-extras" yet?  If not, open a terminal window and install that and let us know what happens.

---

### Post by trikster_x on 2010-12-08
I have that installed already.  I actually had flash based audio working fine for a while prior to this and have not changed any settings on my computer.

I have been running 10.04 on this comp since early October, sorry I didn't mention any of that sooner.

---

