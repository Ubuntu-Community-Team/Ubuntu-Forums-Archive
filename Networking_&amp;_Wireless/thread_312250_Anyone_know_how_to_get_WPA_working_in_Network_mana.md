---
title: "Anyone know how to get WPA working in Network manager"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by waynepr72 on 2006-12-04
Hi there,

I have successfully got WEP working using the following card below on Ubuntu, I really want to be able to use WPA to make this more secure. Does anyone know how to get Network manager to give the option in the drop down box to set this up.  I have read many threads on manually editing config files but I would rather use the GUI screen to configure, there seems too many variations in the edits to manually set this up and get working.

_______________________________________________________________
0000:06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
Subsystem: Atheros Communications, Inc.: Unknown device 1051
Flags: bus master, medium devsel, latency 168, IRQ 11
Memory at 26000000 (32-bit, non-prefetchable) [size=64K]
Capabilities: [44] Power Management version 2
________________________________________________________________

Has anyone successfully done this or is it going to be hours of playing with conf files to get this security to work? I am currently using the Drapper 6.06 release on my laptop.

Thanks in advance,

Wayne

---

### Post by johncro13 on 2006-12-05
I'll tell ya, this entire process of working with network manager to support wpa is a ton easier in edgy.  I highly suggest keeping your wep for the time being, upgrade and then install network manager.

It worked just fine for me for a long time...

---

