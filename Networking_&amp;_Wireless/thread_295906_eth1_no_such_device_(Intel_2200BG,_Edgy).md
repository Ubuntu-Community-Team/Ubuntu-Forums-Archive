---
title: "eth1: no such device (Intel 2200BG, Edgy)"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by kungfoofool on 2006-11-08
I rebooted. That's ALL I did. I swear. It came back up, and now my wireless card has ceased to function. Before, it was eth1. Now when I restart I get:

```

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

```

I checked the device manager, and my wireless card is listed. lspci shows:

```

03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Intel Corporation Unknown device 2721
        Flags: medium devsel, IRQ 177
        Memory at dfdfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

```

What did I do, and how can I fix it? I've been running Ubuntu since 5.10 and I've never had a problem like this. I don't even know how to start to fix such a random problem.

---

### Post by kungfoofool on 2006-11-08
I ran lshw and got this:

```

          *-network:1 UNCLAIMED
                description: Network controller
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@03:03.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:dfdfd000-dfdfdfff irq:177

```

---

### Post by elektronaut on 2006-11-09
Just a guess, as I'm also having a [strange problem with my wireless card]("http://ubuntuforums.org/showthread.php?t=295113"): Maybe it's a hardware issue and the card has to be activated by some switch or in the BIOS?

---

### Post by kungfoofool on 2006-11-09
Well, I resolved it. I rebooted into Windows (it's a dual boot system) and rebooted back into Ubuntu and, lo! It worked. 

I don't know what the heck I did to break it OR to fix it.

I could expect that out of *Microsoft*, but Ubuntu? It saddens me.

---

### Post by elektronaut on 2006-11-09
I read somewhere that people were noticing this: If they shut down Windows having no wireless connection and booting into Ubuntu afterwards, they had no wireless connection there. If wireless was activated when shutting down Windows, they could also use the wireless interface in Ubuntu. So it seems as if Windows is issuing some hardware call (to the BIOS?) to deactivate the wireless card, and Ubuntu is not able to change this afterwards.

You shouldn't blame this on Ubuntu, it's probably like this because Microsoft is in close alliance with the laptop manufacturers, and they have possibilities to access stuff that the Linux community doesn't have.

---

### Post by DannyG on 2006-11-09
I wouldn't blame this on Ubuntu either, if indeed booting into Windows fixed the problem, you can more or less bet that Windows caused the problem in the first place...

---

