---
title: "Wireless occasionally stops working"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by chandler on 2007-12-06
It's a Sony Vaio VGNNR110E laptop and my connection goes in and out.  Quite frequently (every 2 hours)

The device is LAN-Express AS IEEE 802.11g PCI-E Adapter
The router I connect to is a Linksys WRT54GS with 1.02.2 firmware.

I'm using NDISWrapper
```
william tux ~ $ sudo ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
```

I've noticed one thing in particular, when it is working, lspci lists
```
william tux ~ $ lspci | grep Atheros
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

When it is not working, the rev part changes from 01 to ff...

ndiswrapper version is ```
william tux ~ $ ndiswrapper -v
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko
version:        1.49
vermagic:       2.6.22-14-generic SMP mod_unload 586 
```

---

