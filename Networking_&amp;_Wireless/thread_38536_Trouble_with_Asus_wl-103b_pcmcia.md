---
title: "Trouble with Asus wl-103b pcmcia"
date: 2005-05-31
forum: Networking &amp; Wireless
---

### Post by QuantumCowboy on 2005-05-31
Hello all, I am having some trouble with wireless networking.  I have tried everything that seems relevant on this forum and i'm still having trouble.

Asus wl-103b using Broadcom driver (bcmwl5) on HP Pavilion zv5000, amd64, nvdivia.

I followed the ndiswrapper howto wiki, which worked except that ndiswrapper -l returns *bcmwl5  driver present* but not [i]hardware present[i] like I want.  I thus figured the problem was some hardware quirk with the laptop.  On the Mepis Linux forums someone was saying how the memory windows are different for the zv5000, and this was corroborated by [http://web.purplefrog.com/~thoth/zv5000/](http://web.purplefrog.com/~thoth/zv5000/) (which is for gentoo on zv5000).  The memory windows they had also fit with what my [i]lspci -v[i] is telling me:

> 0000:02:04.1 CardBus bridge: Texas Instruments: Unknown device ac54 (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 006d
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at e0105000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: e1000000-e13ff000 (prefetchable)
        Memory window 1: e0c00000-e0fff000
        I/O window 0: 00006000-00006fff
        I/O window 1: 00005000-00005fff
        16-bit legacy interface ports at 0001

As suggested I changed my /etc/pcmcia/config.opts to:

> include port 0x6000-0x6fff
include port 0x5000-0x5fff
include memory 0xe1000000-0xe13ff000
include memory 0xe0c00000-0xe0fff000

The card still does not light up on boot however, and [i]modprobe ndiswrapper[\i] does not activcate the card either.  I am at a loss as to how I should proceed now, and would appreciate any help.

Thanks
QC.

---

