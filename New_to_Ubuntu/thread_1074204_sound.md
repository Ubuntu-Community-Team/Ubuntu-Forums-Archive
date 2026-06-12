---
title: "sound"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by bud_man on 2009-02-18
i know that this might have been posted before but, i have no sound whatsoever on my computer and i'm completely stumped on what to do.
i thought that maybe this would help:

root@bud-laptop:~# lspci -v
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff01
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: oss_hdaudio

root@bud-laptop:~# aplay -l
aplay: device_list:215: no soundcards found...

i'm pretty much new to linux so, any kind of help is appreciated!

thanks!

---

### Post by handy on 2009-02-19
This how-to may get you out of trouble:

*_[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)_*

---

