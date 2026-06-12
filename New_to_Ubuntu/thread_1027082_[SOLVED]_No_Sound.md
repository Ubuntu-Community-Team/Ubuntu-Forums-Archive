---
title: "[SOLVED] No Sound"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by bigal1932flying on 2008-12-31
After suffering much frustration with Intrepid Ibex I decided to switch back to Hardy Heron. I did a fresh install and downloaded and installed 322 updates. But now find I have no sound.
Can someone please tell me how to fix this problem before I go completely round the twist.
Thanks a million in advance.

---

### Post by nhasian on 2008-12-31
I trust your speakers are turned on and you have checked the volume sliders in the audio mixer?  lets start troubleshooting with:

```
lshw -C multimedia
```

---

### Post by bigal1932flying on 2009-01-01
Ran that command output:
 *-multimedia:0          
       description: Multimedia audio controller
       product: AC'97 Sound Controller
       vendor: Silicon Integrated Systems [SiS]
       physical id: 2.7
       bus info: pci@0000:00:02.7
       version: a0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
  *-multimedia:1
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20 module=cx8800
Don't know what all this means.

---

### Post by abn91c on 2009-01-01
first try aplay -l
try sudo modprobe snd-cx8800

---

