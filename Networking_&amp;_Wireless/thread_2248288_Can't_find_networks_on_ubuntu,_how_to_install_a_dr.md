---
title: "Can't find networks on ubuntu, how to install a driver without internet?"
date: 2014-10-13
forum: Networking &amp; Wireless
---

### Post by Lex_Bjerkeli on 2014-10-13
Hello! 
I just got Ubuntu 14.04 on my laptop, but I have no internet connection. 
 
I do have a laptop, "HP ProBook 6475b" with the network card "Broadcom 802.11n" 
 
I do not know how I can install drivers for ubuntu though, anyone willing to help? 
 
Though the thing is, I don't have a wired connection available, nor do I have a USB Stick. 
If I have to download anything, can't I just download it on the windows partition, and grab it from the linux partition? 
 
(Have both Linux and Windows on the laptop, on different partitions)

---

### Post by Bucky Ball on 2014-10-13
*Thread moved to **Networking & Wireless**.*

Welcome. Please open a terminal and input this command:

```

sudo lshw -C network
```

Post the output back here.

---

### Post by Lex_Bjerkeli on 2014-10-13
The output I got was: 

>   *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 07
       serial: a4:5d:36:5b:25:8b
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:54 ioport:5000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Network controller
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:19 memory:d5000000-d5003fff



---

### Post by Bucky Ball on 2014-10-13
Try [THIS]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access"). Good luck.

---

### Post by Lex_Bjerkeli on 2014-10-13
Ahh! After almost 2 hours of not understanding too much of the website, I figured it out
Since it went on the Physical CD copy of Ubuntu I just had errors all over the place, but once I mounted the ISO file I had on my windows partition I found the neccesary files.

Thank you so much!
It's much appreciated.

---

### Post by Bucky Ball on 2014-10-13
Not a problem and excellent news! Nice work figuring it out. Good luck and enjoy. ;)

---

