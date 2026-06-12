---
title: "Linksys wireless card did not work with 8.04 LTS"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by garyTX on 2008-05-08
Installed version 7.10 months ago and always included updates along the way.  Never had to use ndiswrapper.  Had no problems with my Linksys wireless PCI card working OK with WEP encryption.  Upgraded to 8.04 and my wireless capability quit working altogether.  I followed troubleshooting guides from ubuntu.com to check for driver, device, ipv6, etc., but the Linksys card could not reach the router.  BTW, this guide says to go to SYSTEM->PREFERENCES -> HARDWARE INFORMATION, but there is no “HARDWARE INFORMATION” menu item!  After much frustration, I finally hit the ESC key during the reboot sequence to get a chance to boot from an older version (see list from “/boot” below).  Sure enough, I booted from the next older version (config-2.6.22-14-generic), and had no problem with my wireless card.  The version associated with config-2.6.24-16-generic is the version that did not work. After that good reboot from the older version, the output from the command “lshw –C network” follows (network:1 is the wireless card).  

**What can I do to fix this?**

_Output from “lshw –C network” after booting from older version:_
  *-network:0
       description: Ethernet interface
       product: LNE100TX
       vendor: Lite-On Communications Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 21
       serial: 00:a0:cc:3f:31:1c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 module=tulip multicast=yes
  *-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: wmaster0
       version: 01
       serial: 00:0f:66:e6:b6:e8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.103 latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g

[U]
/boot directory list:[/U]
total 45212
-rw-r--r-- 1 root root  414274 2007-09-23 15:28 abi-2.6.20-16-generic
-rw-r--r-- 1 root root  424317 2008-02-12 04:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root  422607 2008-04-10 11:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root   83217 2007-09-23 12:47 config-2.6.20-16-generic
-rw-r--r-- 1 root root   75311 2008-02-12 04:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root   79964 2008-04-10 11:51 config-2.6.24-16-generic
drwxr-xr-x 2 root root    4096 2008-05-03 00:58 grub
-rw-r--r-- 1 root root 6916583 2007-10-22 17:17 initrd.img-2.6.20-16-generic
-rw-r--r-- 1 root root 7261058 2008-02-28 23:02 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root 7261017 2008-02-14 20:26 initrd.img-2.6.22-14 generic.bak
-rw-r--r-- 1 root root 7575145 2008-05-03 01:09 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7575154 2008-05-03 00:58 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 05:06 memtest86+.bin
-rw-r--r-- 1 root root  807071 2007-09-23 15:30 System.map-2.6.20-16-generic
-rw-r--r-- 1 root root  823535 2008-02-12 04:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root  899892 2008-04-10 11:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root 1747372 2007-09-23 15:28 vmlinuz-2.6.20-16-generic
-rw-r--r-- 1 root root 1764536 2008-02-12 04:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 11:51 vmlinuz-2.6.24-16-generic

---

