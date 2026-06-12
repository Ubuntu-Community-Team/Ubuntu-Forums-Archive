---
title: "Ethernet connected but stops working after one website"
date: 2016-02-27
forum: Networking &amp; Wireless
---

### Post by brandon45 on 2016-02-27
Hey guys I just installed 14.04 I have a IP on eth0 and I can browse to one website and after that everything stops it still retains the IP but I do not have any internet connection. The wireless connection works fine however. 


lrwxrwxrwx 1 root root 29 Feb 27 18:21 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
brandon@Linux:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT5390R 802.11bgn PCIe Wireless Network Adapter
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: a4:17:31:37:95:c6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.2.0-30-generic firmware=0.34 ip=200.10.1.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f7d00000-f7d0ffff
  *-network
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 08
       serial: 70:54:d2:0c:e9:5d
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:31 memory:f7c00000-f7c3ffff ioport:d000(size=128)

---

