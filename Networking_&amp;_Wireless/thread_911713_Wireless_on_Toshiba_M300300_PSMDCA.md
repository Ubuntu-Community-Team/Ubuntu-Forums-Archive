---
title: "Wireless on Toshiba M300/300 PSMDCA"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by moofasa on 2008-09-05
Hi, I have just installed 8.04 on my new Toshiba laptop and everything is going fine except the wireless. I have been reading the forums and still am not sure exactly what to do. I get the following messages:

```
~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 16
       serial: 00:1e:68:a4:77:ae
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.2.242 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
```

and ```
~$ dmesg | grep Wireless
``` returns nothing..

The Toshiba site only tells me it's an Intel 802.11 a/g/n card and the Vista install seems to have been destroyed when I installed Ubuntu so I can't check the driver it's using in there.

Any help would be appreciated!

Thanks

---

### Post by Stickiler on 2009-09-27
install ubuntu 9.04, the driver comes standard.

---

