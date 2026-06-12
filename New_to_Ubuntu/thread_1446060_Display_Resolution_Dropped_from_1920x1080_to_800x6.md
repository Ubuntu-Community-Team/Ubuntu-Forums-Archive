---
title: "Display Resolution Dropped from 1920x1080 to 800x600"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by Ben G on 2010-04-03
I'm having some trouble with my display. I bought a new monitor about two months ago which was automatically detected by Ubuntu 9.10 and the resolution was set to the correct value 1920x1080.

When I started my PC this morning though the resolution has dropped to 800x600 and there is no higher option available when I open the display manager.

There is no xorg.conf file in /etc/X11 which I thought was unusual but after a bit of reading this seems normal for 9.10?

I have tried to reconfigure x, i.e. "sudo dpkg-reconfigure xserver-xorg" but it didn't work.

Here is the video driver information when I run lspci -v.

```

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
	Subsystem: Fujitsu Technology Solutions Device 1084
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0080000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 2000 [size=8]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0040000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

```

I haven't made any recent changes to the display settings so I'm a bit puzzled as to why this happened. I would really appreciate any of your suggestions as I have no idea what to try next.

---

### Post by Gone fishing on 2010-04-03
I've seen this happen when the cable isn't fully pushed into the video card.

---

### Post by Ben G on 2010-04-03
Thank you very much. First thing I did was try another monitor which had the same problem so I didn't think the cable was the problem. I checked again at the video card end though after I seen your reply and it must have been slightly loose as I pushed it in, restarted and the display is back to normal.

---

