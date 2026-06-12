---
title: "Linksys WPC54G on 8.04"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by itzig on 2008-05-11
Hello, I just upgraded to 8.04, and now I am trying to get my wireless card working (Linksys WPC54G)
I am using the trouble shooting guide first:
[https://help.ubuntu.com/8.04/interne/C/troubleshooting.html#troubleshooting-driver](https://help.ubuntu.com/8.04/interne/C/troubleshooting.html#troubleshooting-driver)
It says to look for a divice manager, but there is no such thing, I can only find a mod for 'hardware testing". The results are:

3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

looks like it can see it, then I do:
lshw -C network
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:02:60:4c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:11
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth1
       version: 78
       serial: 00:06:5b:d3:46:0e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half ip=192.168.0.10 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth2
       serial: 00:0c:41:2c:32:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

It seems to be disabled, how can I turn it on?

---

### Post by kevdog on 2008-05-11
Seems like another victim of the broadcom ssb bug.  My recommendation would be ndiswrapper with "the hardy bug fix" as per this thread:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by itzig on 2008-05-12
thank you, I will try that once I reinstall this oS. Upgrading to 8.04 didn't go as smooth as I thought. Things are a bid weird. I'll check back here later!

peacin
I

---

