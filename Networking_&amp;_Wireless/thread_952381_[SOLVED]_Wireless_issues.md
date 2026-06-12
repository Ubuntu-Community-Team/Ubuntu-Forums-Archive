---
title: "[SOLVED] Wireless issues"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by dj34 on 2008-10-19
Newbie here. I am trying to get my wireless card to work can somebody please help me?
 When I use lshw -C network, I get:
work:~$ sudo lshw -C network
[sudo] password for dj34: 
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:21:d9:30
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.15.101 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
When I use iwconfig, I get:
-work:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Please assist!

---

