---
title: "Dell 1370 and Hardy Heron"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by -dUb- on 2008-07-25
I've recently set up a dual-boot (XP and Hardy Heron) setup with my laptop.  The reason I've decided to do so is mainly to use Ubuntu for my browsing because two of my friends got infected with nasty viruses not long ago, and I don't want to go through the hassle that they did.  I know that Ubuntu is capable of much more, but want to keep XP until I become more familiar with Ubuntu. 
Besides the slight learning curve, everything was going fine since I hardwire to the internet while I'm at home.  Then I tried to use my wireless and realized that I couldn't connect.  I googled and couldn't find any good instructions (most assume that you know more than I do, and don't really break it down step-by-step) besides this link... [http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper) .  The problem is that the instructions are for Feisty Fawn and won't work for Hardy Heron. 
1st question is.. Can anyone take the time to edit these instructions for use with Hardy Heron for me?  It would be greatly appreciated.  
2nd question is...  If I do follow the instructions and get it working, will it disable my ability to use wireless when I boot to Windows XP?

---

### Post by superprash2003 on 2008-07-25
in your terminal type lshw -C network and post output here..

---

### Post by -dUb- on 2008-07-25
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:14:22:c8:06:fe
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.2.5 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:76:ad:42
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by superprash2003 on 2008-07-25
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by -dUb- on 2008-07-30
Thanks a lot superprash2003.  I finally got around to trying it out.  The instructions in the link worked flawlessly.  Wireless works after reboot, and I even checked wireless while booted into XP.  If we were in jail, I'd protect you in the shower.

---

