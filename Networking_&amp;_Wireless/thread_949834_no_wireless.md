---
title: "no wireless"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by torino351 on 2008-10-16
Hey guys I am new to Linux. I cant get the wireless internet to work I can only get wired on my laptop. I posted what shows up after typing sudo lshw -C network below if that can help out at all. Its version 8.04 32 bit by the way. 

If any one could help me out I would appreciated it alot.
Gunnar Johnson




gunnar@gunnar-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 13
       serial: 00:1d:ba:1a:be:90
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s

---

