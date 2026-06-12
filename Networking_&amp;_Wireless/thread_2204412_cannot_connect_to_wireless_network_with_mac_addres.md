---
title: "cannot connect to wireless network with mac address filtering enabled"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by josh35 on 2014-02-08
Hi All, 

I have the following wireless card (lspci)

04:01.0 Network controller: Atheros Communications Inc. AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn] (rev 01)

This card works fine using the Elementary ( a variant of ubuntu) linux distro when mac address filtering is off.- however it does not work when I enable the mac address client filtering in the router, even though the rrouters settings have not been changed and my mac adddress is listed as allowed.

the wireless network icon also keeps flashing and continiously asks me to input the password again and again. 

Can someone also confirm for me which channels this wirless card has the ability to interpret and connect to, i.e. %gz or 2.4 or both? as we have dual band router, from memory it can only connect to one.

If this doesnt work can anyone suggest a really lightweight distro which is quite simple I am medium new at linux.

josh@JOSHUA-PC:~$ sudo lshw -c network
[sudo] password for josh: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:7d:a1:d9:2a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.110 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:e9000000-e9000fff memory:80000000-8001ffff
  *-network
       description: Wireless interface
       product: AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn]
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wlan0
       version: 01
       serial: 00:22:6b:a1:9d:bd
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-51-generic-pae firmware=N/A latency=168 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:ea000000-ea00ffff
josh@JOSHUA-PC:~$

---

