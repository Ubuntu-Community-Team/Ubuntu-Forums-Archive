---
title: "No Sound at all..."
date: 2010-09-09
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2010-09-09
I didn't change anything, but I have no sound from laptop speakers or headphones, possibly happened after recent updates but I'm not sure.  GUI for alsamixer shows master and PCM set up, and nothing is muted...

Any ideas?

---

### Post by x C0MMAND0 x on 2010-09-09
aplay -l returns

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

dmesg |grep HDA returns

```
[   14.689083] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.689134] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.813828] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   15.362759] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   15.362842] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   15.362900] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
```

lspci -v (for audio) returns

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 0209
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f6ffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

---

### Post by x C0MMAND0 x on 2010-09-10
*Bump* Any ideas?

---

### Post by x C0MMAND0 x on 2010-09-10
Is there a way to reset all audio configs back to normal?  I already ran 

```
sudo apt-get purge pulseaudio && sudo apt-get install pulseaudio
```

---

