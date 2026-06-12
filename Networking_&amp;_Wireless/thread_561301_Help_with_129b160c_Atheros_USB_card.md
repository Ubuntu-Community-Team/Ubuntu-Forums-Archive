---
title: "Help with 129b:160c Atheros USB card"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by Josh04 on 2007-09-27
Okay, I have a Siemens Gigaset 108 USB wireless adapter, which uses the Atheros 5523 chipset. I've had it working for about 6 months now with ndiswrapper (1.48, because there's a bug in the repo version which makes it hang if unplugged), despite it having a USB id of 129b:160c rather than the apparently more common 129b:160b.

However, I've just reinstalled Ubuntu due to a crazy file system problem, and I can't get the card working again. The Windows drivers for it install, and the device is detected and networks show up in nm-applet. If I select one though, it hangs the moment I've pressed Okay on the network key. Same if I do it without network manager. No errors show up in dmesg or syslog; it just hangs.

Any ideas?

---

