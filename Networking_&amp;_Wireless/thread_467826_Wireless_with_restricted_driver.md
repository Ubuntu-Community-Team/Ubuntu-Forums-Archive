---
title: "Wireless with restricted driver"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by Pathian on 2007-06-08
Hello all,
I recently used the update manager to update my install from dapper to edgy and from edgy to feisty. My wireless worked normally under Edgy, but it stopped working under Feisty. 
       On first boot, it gave me a warning about restricted drivers that were in use. My wireless connection is "active", ie. it can see my wireless network, however it cannot connect to it. Since this happened after an update, I assumed it "broke" because of a newly updated package. Is there anyway way I can just roll back a package or change a setting to get things working again?  

Here is the relevant result of my lspci -v 

02:06.0 Ethernet controller: Atheros Communications, Inc. AR5211 802.11ab NIC (rev 01)
      Subsystem: AMBIT Microsystem Corp. Unknown device 0400
      Flags: bus master, medium devsel, latency 168 IRQ 23
      Memory at e0200000 (32 bit, non-prefetchable) [size=64k]
      Capabilities: <access denied>

Thanks much!

---

