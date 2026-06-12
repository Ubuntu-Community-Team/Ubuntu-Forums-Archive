---
title: "Ralink modules performance (specifically rt61pci)"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by Melcar on 2008-02-15
Quick question.  Are the Ralink supposed to be incredibly slow?  I have two PCI wireless adapters, both using the rt61pci module, and compared to ndiswrapper, download/upload speeds are ridiculously slow.  Other devices that I have used with the default kernel modules, while still not as fast as when using ndiswrapper, perform decently.  Is there something I'm missing, or maybe something I can do to improve speeds, or are these modules just bad?

---

### Post by rustybronco on 2008-02-15
> **Melcar said:**
>  or are these modules just bad?Not that I know of.
>  *-network
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:b6:59:90:aa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.3 latency=64 mod
my download speed is 158-160kb/s on anything I throw at my dsl, windows or linx no matter the card used.

---

### Post by magomago on 2008-04-09
i am experiencing the same problems when it comes to speed.  I'm getting about 5mbps right now and unsure how to kick this speed up.  Thanks =)

---

