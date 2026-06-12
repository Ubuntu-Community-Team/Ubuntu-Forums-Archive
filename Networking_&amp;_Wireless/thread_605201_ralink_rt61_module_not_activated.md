---
title: "ralink rt61 module not activated"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by JebusWankel on 2007-11-06
I've been following this [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61) and I've gotten as far as activating the new module and deactivating the old module using modprobe, but the new module didn't get activated because iwconfig returns > ra0       no wireless extensions.

The only thing I've done differently from the guide is I've used a newer version of the driver (v1.1.1.0 vs 1.1.0.0). It seems like everything else has worked so far.
also:
$ lsmod | grep rt61
rt61pci                24576  0 
rt2x00pci              11520  1 rt61pci
rt2x00lib              19584  2 rt61pci,rt2x00pci
eeprom_93cx6            3200  1 rt61pci
rt61                  243716  0 
mac80211              171016  4 rt61pci,rt2x00pci,rt2x00lib,rc80211_simple

so I guess the zeros mean the modules aren't active.

---

