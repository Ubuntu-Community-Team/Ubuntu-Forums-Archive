---
title: "RealTek RTL8169S-32 (Linksys Gigabit Ethernet)"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by chezmojo on 2008-04-26
I just bought a Linksys EG1032V3 Gigabit Ethernet adapter after my Intel pro died (for whatever reason Ethernet cards keep dying on me)... Anyway, it has the Realtek RTL8169S-32 chip, which is supposed to be suported by the r8169 kernel module, however the computer sees the card as:

lspci:```

05:06.0 Ethernet controller: Third Planet Publishing Unknown device 1032 (rev 10)
        Subsystem: Third Planet Publishing Unknown device 0024
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 12
        I/O ports at a000 [size=256]
        Memory at c5010000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at c4000000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2
```
lshw:```

  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: Third Planet Publishing
       vendor: Third Planet Publishing
       physical id: 6
       bus info: pci@0000:05:06.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32

```
There is no mention Realtek, Linksys, etc. and as such the kernel simply doesn't see this as an r8169 device (manually loading the module does nothing and the r8169 driver from Realtek doesn't compile).

So is this card reporting itself incorrectly? Is it broken? Is there a way to trick the kernel into using this card?

Here's some info on my computer:

2.6.24-16-server SMP x86_64
Ubuntu 8.04

---

