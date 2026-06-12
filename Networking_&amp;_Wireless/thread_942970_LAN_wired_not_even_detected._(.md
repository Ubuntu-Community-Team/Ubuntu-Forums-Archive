---
title: "LAN wired not even detected. :("
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by shane2peru on 2008-10-09
Ok, I have used Ubuntu since Breezy days, and have never run into a eth0 card that was not recognized.  I managed to get my wireless working, as there are more posts in reguards to the wireless now working.  At any rates, I'm working on a brand new laptop (Toshiba M305D-S4830 AMD Turion X2 ultra 64 with 4GB of ram)  Running 64bit Ubuntu (however 32bit didn't recognize anything either).  Here is the output of a command that I found searching the forums it didn't help me much perhaps it will help someone else determine the problem:
```

 sudo lshw -C network

  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:21:63:17:4c:8e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=10.1.10.73 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```
If anyone has any ideas I would greatly appreciate the help. Thanks!

Shane

---

### Post by shane2peru on 2008-10-10
Wow this made it to page 4 without a single reply!  I didn't think it was that complex of a problem.

Shane

---

