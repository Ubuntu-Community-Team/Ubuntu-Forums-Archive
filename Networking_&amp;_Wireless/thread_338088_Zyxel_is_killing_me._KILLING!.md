---
title: "Zyxel is killing me. KILLING!"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by giladg on 2007-01-13
Hi,

Super new to ubuntu, know my way generally in unix.

Got a Zyxel G-302 wireless pci card, realtek chipset 8185L (at it says on the chip).
Can't make it work after reading many posts here and around the web.

Tried ndiswrapper and also the driver that came with the installation CD (which requires compiling, an attempt what failed miserably)

Where do I start debugging?

Linksys Router set to no security/MAC filter list enabled.
ndiswrapper -l sais driver invalid on the net8185 driver I installed.
blacklisted acx, included ndiswrapper in modules list. ndiswrapper seems to load ok.

lspci -X returns 'unknown device 8185' on the Ethernet Controller line.

Using 6.06/32bit intel 733MHz.

Anyone?

Thanks,
Gilad.

---

