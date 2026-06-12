---
title: "WICD &amp; ndiswrapper - help!"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by kiisu on 2008-04-24
NetworkManager was giving me alot of headaches recently so I've decided to give WICD a try.
Installed it no problem but so far only my wired connection works. I've always had to run my wireless card through ndiswrapper and so far it isn't showing up in this program.
What should I do to get it to recognise? Would it be advisable to redo my ndiswrapper & driver?

Here's my lshw if it helps:

 > lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:18:9b:67
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.51+,11/15/2006,5.1.1.9 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:fd:be:eb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.105 latency=0 module=r8169 multicast=yes
kvm@kvml:~$ 

---

### Post by kiisu on 2008-04-24
After some changes in the preferences of WICD and a restart wireless seems to be working, but I'll return if theres problems.

I'm interested to see if this really is more reliable than network manager.

---

