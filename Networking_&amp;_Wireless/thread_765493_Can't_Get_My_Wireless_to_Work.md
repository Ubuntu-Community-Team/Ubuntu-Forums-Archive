---
title: "Can't Get My Wireless to Work"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by Jenga-kun on 2008-04-24
I installed Hardy Heron not to long ago and so far I'm really liking it except that my wireless isn't working. I'm trying to fix it by following the instructions here: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) but when I type this: lshw -C network into terminal I get this:

jesse@jesse-laptop:~$ sudo lshw -C network
[sudo] password for jesse: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:97:5e:6d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:24:bd:f2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

which I think tells me that I have no drivers installed for my wireless card. Now I don't know what to do. I'm considering installing one of the drivers from here: [http://linuxwireless.sipsolutions.net/en/users/Drivers/b43](http://linuxwireless.sipsolutions.net/en/users/Drivers/b43) but I don't know which one of the four drivers to install.

---

### Post by Jenga-kun on 2008-04-25
I could use all the help I can get.

---

