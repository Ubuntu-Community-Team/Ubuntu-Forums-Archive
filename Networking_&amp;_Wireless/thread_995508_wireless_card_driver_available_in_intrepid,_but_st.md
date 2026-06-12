---
title: "wireless card driver available in intrepid, but still not working"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by le_vainqueur on 2008-11-27
I just made a fresh install of Intrepid on my laptop.  When I got it booted up, I was  excited because it said that there's a proprietary driver for my wireless card.  It was activated by default, but wireless is still not working.  In the "proprietary drivers" window, the driver is listed as:

> Support for Atheros 802.11 wireless LAN cards.

When I was in Hardy, the following thread helped me to get my card working, but I don't want to go through complicated steps to fix the problem if there's already a driver available.  

> [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

==================================

I ran the command "lspci -v | less" and got the following:

> 03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Device 137a
        Flags: fast devsel, IRQ 19
        Memory at f6000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel modules: ath_pci


---

### Post by le_vainqueur on 2008-11-28
I got the problem fixed using this thread:

> [http://ubuntuforums.org/showthread.php?t=940048](http://ubuntuforums.org/showthread.php?t=940048)

The post that I found useful was #4 (installing linux-backports-modules-intrepid).  Everything worked fine after that.  Glad to see things are getting easier with newer distros

---

