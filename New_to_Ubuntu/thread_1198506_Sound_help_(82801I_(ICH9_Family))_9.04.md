---
title: "Sound help (82801I (ICH9 Family)) 9.04"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by yang925 on 2009-06-27
I recently brought a dell open sources inspiron 15N computer. The sound worked fine, it was Ubuntu 8.10 with gnome. I upgraded to Kubuntu 9.04 with KDE 4.3 Beta 2. I love KDE. haha. So after a couple of Keneral Upgrades the sound isn't working.  

lspci sound:
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Dell Device 02aa
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f6afc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

aplay -l
```

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

volumes at 95% no sound. This is a laptop but hardware kill sound brings sound to 0%.

---

### Post by yang925 on 2009-06-27
anyone?

---

### Post by yang925 on 2009-06-28
no one?

---

### Post by karthik17 on 2009-09-05
i'm also having the same prob .... pls help us out !!!

---

### Post by new4me on 2009-09-05
open a console, type in alsamixer and check to see that nothing is muted.

arrow keys move you through the differnet selections and the tab key moves you to the next page.

later 
J

---

