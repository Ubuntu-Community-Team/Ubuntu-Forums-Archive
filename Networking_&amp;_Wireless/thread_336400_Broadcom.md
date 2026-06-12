---
title: "Broadcom"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by spixx on 2007-01-11
Hello another problem with Wireless card. I have a Broadcom 4311 (?) 54 Mbps wireless integrated  card (hp compaq 6310nx) on unbuntu 6.10. the thing is my wireless connection is deactivated and when you logg in w/ admin and activate it, the thing just shuts down again. It were working (or the thing was at least active) before i installed Java5 jdk

What is the trouble?
08:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1364
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at e8000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

is what it says when running: lspci -v | less

---

### Post by scrooge_74 on 2007-01-11
Did you check this thread? [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

### Post by discord on 2007-01-25
look here got it working and with network manager!

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

