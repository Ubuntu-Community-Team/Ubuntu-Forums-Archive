---
title: "wireless issues"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by splashnet on 2008-07-26
just downloaded my first non windows os (ubuntu 804) cant get wireless working. im aware of this : [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo). but i honestly dont understand these instructions. my net adapter is:  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter. a detailed rundown or an all in one wiki link would be helpful cause im really lost with this os (i only downloaded it because i hate vista)

---

### Post by superprash2003 on 2008-07-26
in your terminal type iwconfig and post output.. also type lshw -C network

---

### Post by splashnet on 2008-07-27
lo        no wireless extensions.

eth0      no wireless extensions.



 lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:89:9a:51
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.124 latency=0 module=r8169 multicast=yes

---

### Post by superprash2003 on 2008-07-28
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)
[http://lampcomputing.com/getting-ar2...-work-fedora-9](http://lampcomputing.com/getting-ar2...-work-fedora-9)

---

