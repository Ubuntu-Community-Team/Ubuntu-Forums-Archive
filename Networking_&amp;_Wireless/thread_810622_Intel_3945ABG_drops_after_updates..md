---
title: "Intel 3945ABG drops after updates."
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by bentrafford on 2008-05-28
My 3945ABG wireless card on my Dell Inspiron 9400 keeps dropping after I update with 8.04 (which I installed cleanly a short while back). The last time this happened, I installed the backports modules, and that fixed it.

*sudo lshw -C network* gives me the following:

 ```
 *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:f7:1f:18
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.102 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
```

uname -a gives me this:

```
Linux BensLaptop 2.6.24-17-386 #1 Thu May 1 13:57:56 UTC 2008 i686 GNU/Linux
```

Any advice?

---

