---
title: "need help with my ATHEROS AR5006EG 802.11 b/g Wireless"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by ryudo423 on 2007-12-16
HI IVE BEEN TRYING FOR HOURS AND HAVE NO LUCK..PLEASE HELP..
UP WHERE I MANEGE MY NETWORKS IT DOESN NOT SAY ENEABLE WIRELESS AND MY LIGHT IS NOT ON..IM USING AN ACER ASPIRE 3680..

heres what i get when i run lshw

steve@steve-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:3b:e2:0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.1.104 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by Vic! on 2007-12-19
[http://ubuntuforums.org/showthread.php?t=643750](http://ubuntuforums.org/showthread.php?t=643750) look through that, maybe we can figure this one out... 2 heads better than 1.

---

