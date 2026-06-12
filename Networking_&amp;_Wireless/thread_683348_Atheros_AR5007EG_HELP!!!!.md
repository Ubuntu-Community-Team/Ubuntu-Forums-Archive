---
title: "Atheros AR5007EG HELP!!!!"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by Aglystas on 2008-01-30
Hello everyone,
    I know this has been posted many times prior, but I'm hoping a guru will reply to me and help a fellow ubuntu user out.  I've read through the HOWTO for this card already and got as far as successfully installing the net5211.inf driver successfully(as far as I can tell).  I then attempted to connect and could not see my wireless as an option in the network manager, this turned out to be a simple press of (fn+f2) to turn the wireless on.  No my big issue is that I can't see any networks to connect to.  I know that they exist I can see 2 networks (mine and neighbors) in my ubuntu destop at present.  I attempted using wicd, but that also does not see any of the networks.  I'm running a 7.10-64 bit on an asus A8D laptop.  My wireless is the Atheros AR5007EG using ndiswrapper+net5211.inf

emiller@asusBox:~$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)


emiller@asusBox:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:60:16:ec:12
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.60 ip=192.168.2.53 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:49:52:7c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.45+,06/21/2007,5.3.0.56 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Anyone that can help, I would be greatly appreciated.

---

