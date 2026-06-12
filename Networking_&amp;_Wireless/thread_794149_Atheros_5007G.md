---
title: "Atheros 5007G"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by micho119 on 2008-05-14
Hi all,
I need a driver for my wireless card
Atheros 5007g
its on compaq presario laptop
and my ubuntu is 8.04 (latest edition)
I hope you can help me
thanx

---

### Post by balagosa on 2008-05-14
first of all, please list complete details **just to be sure.**

can you post the outcome of ```
lspci
``` and ```
lshw -C network
```

as for the meantime, here are some reference: [link 1]("http://ubuntuforums.org/showthread.php?t=766529&highlight=wifi+hardy")

[link 2]("http://ubuntuforums.org/showthread.php?t=512828&highlight=acer+aspire+3680") <---some said this still works even though it is on Feisty.

Note: link 1 uses MadWifi method. link 2 uses Ndiswrapper

---

### Post by st_e_fan on 2008-05-14
[LEFT][/LEFT]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon X2300
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
stefan@stefan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 10
       serial: 00:1e:8c:52:2e:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.65 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
stefan@stefan-laptop:~$ 

I also think that the driver for my ATI X2300(branded X1300) is needed

---

### Post by avtolle on 2008-05-14
It appears you are using the AMD-64 version of Hardy, given the wireless card's detection as AR242x...
The following worked for me on this card and Hardy AMD-64 (scroll down to the instructions for this, about half-way down the page), hope you find it helpful, too.

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

### Post by balagosa on 2008-05-15
> **micho119 said:**
> Hi all,
I need a driver for my wireless card
Atheros 5007g
its on compaq presario laptop
and my ubuntu is 8.04 (latest edition)
I hope you can help me
thanx

hmm...i did forget where i downloaded my 5007g WiFi driver. but i know i still have it in my Hard Disk. i know it is net52ll.inf, and also you need the ".sys" file

---

### Post by nicedude on 2008-05-16
I just made a complete guide to install ar5007 support in 32 bit Hardy correctly with madwifi drivers step by step with links to everything required. It is 100% and will stop any later problems with conflicting restricted drivers as I remove them. If you have 32bit Hardy and a AR5007 Atheros wireless adapter then I would recommend reading my guide. I have seen other posts claiming the Atheros is junk blah blah , but in fact it is one of the best chipsets available for wireless scanning and cracking purposes when used with the madwifi airmon patched drivers ( it also works quite well for normal encrypted networking ). The people who make such claims are ignorant of how to fix their problem so they blame the equipment, instead of learning something and fixing their implementation of the equipment for proper usage. As long as you are willing to use 32bit Hardy ( And I don't see a performance difference in normal use and I tried both ) then my guide will get you going with the best drivers available  for Atheros cards.

Here is the link to my guide
[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

I hope this guide helps all fellow AR5007 users out.

---

