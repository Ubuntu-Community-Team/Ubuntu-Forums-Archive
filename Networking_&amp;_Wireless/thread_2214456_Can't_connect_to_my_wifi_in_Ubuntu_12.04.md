---
title: "Can't connect to my wifi in Ubuntu 12.04"
date: 2014-04-01
forum: Networking &amp; Wireless
---

### Post by ahooper239 on 2014-04-01
Just last night I switched one of my older desktop PCs over to Ubuntu from Windows XP and as soon as I installed it, I realized the wifi didn't work.  So I connected it via Ethernet and followed a bunch of forum posts, guides, etc to get the wireless working and right now, it detects several other wifi networks *except* my own.  If it helps, the model for my router is Medialink MWN-WAPR300N and the wireless adapter is the BCM4306, for which I installed the b43 driver.  And here's what I got from the ```
sudo lshw -c network
```command:

```
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:11:45:c8:6d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 duplex=full firmware=5751-v3.23a ip=192.168.8.127 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:dfcf0000-dfcfffff
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfafe000-dfafffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:7e:9c:ee
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.11.0-19-generic firmware=508.1084 link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by chili555 on 2014-04-01
Did you check the Broadcom wireless sticky at the top?

---

### Post by ahooper239 on 2014-04-01
Didn't even notice that. I'll look there first, thanks.

---

