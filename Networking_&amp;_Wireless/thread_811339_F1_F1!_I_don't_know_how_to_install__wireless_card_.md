---
title: "F1 F1! I don't know how to install  wireless card driver in ubuntu"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by student1990_VN on 2008-05-29
I just start to use Ubuntu8.04, but OS can't detected my wireless card. I don't know how to install driver for it.
I use laptop HP compaq 6520s, i don't know my wireless card's name but here is it information [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c01129679&jumpid=reg_R1002_USEN](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c01129679&jumpid=reg_R1002_USEN)

Wireless support Intel 802.11a/b/g/draft-n, a/b/g, b/g
Broadcom 802.11a/b/g, b/g
Bluetooth 2.0
HP Wireless Assistant 

How can I install driver for my wireless card?( online and offline,give a link to download driver,please !)

Please help me! I just start to use OS Ubuntu.
Thank you!

---

### Post by cdtech on 2008-05-29
Try this command and lets see what you have:
lshw -C network

:popcorn:

---

### Post by krlhc8 on 2008-05-29
Try copying and pasting this command in the terminal (Applications>>Accessories>>Terminal):  

sudo apt-get install b43-fwcutter

This installs the latest fwcutter for the latest b43 drivers.

---

### Post by cdtech on 2008-05-29
This is what I followed to set mine up (looks the same as mine):
[[COLOR="DarkRed"]Broadcom[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")

My output:
```

 lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth712
       version: a2
       serial: 00:00:6c:a5:44:ec
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.60 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:b5:7e:d1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. ip=192.168.1.200 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

Good Luck...

---

### Post by student1990_VN on 2008-05-29
thank you. I will try it !

---

