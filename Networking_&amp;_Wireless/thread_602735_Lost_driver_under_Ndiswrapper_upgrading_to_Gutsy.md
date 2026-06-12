---
title: "Lost driver under Ndiswrapper upgrading to Gutsy"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by JohnBr on 2007-11-04
I've lost my wireless connection following the upgrade to 7.10.
I use a Marvel 88w8335 chipset which worked fine, but now have "invalid driver" returned.  I'm using a tested driver according to the Ndiswrapper list.  I've tried re-installing Ndiswrapper and various other things, but no joy.  Any ideas?

The output I get from typing sudo lshw -C network in the terminal is:

 *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 5
       bus info: pci@0000:00:05.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0c:76:3e:ec:83
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.4 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
john@john-desktop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blac

---

