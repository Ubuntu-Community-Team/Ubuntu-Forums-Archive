---
title: "Wireless blocked"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by ccisty on 2013-12-06
I installed Ubuntu 12.04 on my Asus laptop, no other OS installed
It doesn't have a physical wi fi switch
I can't connect to the Internet by wireless.
Maybe this can help to understand the problem
[QUOTE][        configuration: driver=pcieport
             resources: irq:17 memory:f7d00000-f7dfffff
           *-network DISABLED
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 24:0a:64:4d:7f:01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.8.0-19-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
/QUOTE]
Thanx for your help

---

### Post by chili555 on 2013-12-06
What is the exact model of Asus laptop? Doesn't it have an Fn+Fxx key combination to enable and disable wireless? What does this tell us?```
rfkill list all
```

---

