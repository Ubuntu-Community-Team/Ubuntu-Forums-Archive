---
title: "Belkin f5d7000 install?"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by embolalia1187 on 2008-09-03
I just spent the better half of a day installing Linux (HD problems, long story), and I tried to put in a wireless network card. It wasn't surprising that it isn't working, but I think there's supposed to be a way to make it. I've seen some other threads about it, but I'm having a hard time sifting through what needs to happen to get some of the commands to work. For example, typing ndiswrapper followed by anything tells me ndiswrapper isn't installed. And typing sudo apt-get ndiswrapper (no matter what else I put after it) tells me it can't find it.

**Long story short:** I need to install this card, a belkin wireless G f5d7000, on Ubuntu 8.04LTS. And, to make things more complicated, this is a 64-bit computer.

typing ```
lspci -v | less
``` into the terminal gives me 
```
05:01.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
        Subsystem: Belkin Unknown device 700f
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 1000 [size=256]
        Memory at 90002000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

```
among other things that don't seem relevant.

Thank you for any help!

---

### Post by embolalia1187 on 2008-09-05
Bump? Does anybody know what to do? Is there something I'm missing in how to install ndiswrapper?

---

