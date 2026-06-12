---
title: "Intel 7260 connection issues with high density AP on Ubuntu 14.04"
date: 2014-12-02
forum: Networking &amp; Wireless
---

### Post by mr-shaker on 2014-12-02
I have Thinkpad X240 with Intel wireless 7260 card on Ubuntu 14.04.. please find below the some info about my setup 

```
lshw -C network
*-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 6b
       serial: xxxxxxxxxxxxxx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-031600-generic firmware=25.228.9.0 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
```

When I try to connect to a high density AP the connection never lasts and it shows the following error in demsg 
```
dmesg | grep iwl
iwlwifi 0000:03:00.0: No association and the time event is over already...
```

Please let me know if any further information needed

---

