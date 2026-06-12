---
title: "Ubuntu 8.04 and Hp 6715b wireless problems"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by Quackcandle on 2008-07-14
Hi All

Have just installed Ubuntu 8.04 inside Windows XP on an HP6715b laptop

Installed ndiswrapper and used the wireless card .inf file from HP

The blue wifi light is on but there's no connection to the internet

Turning encryption off doesn't make any difference

Here is the result of lshw -C network:

  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:74:66:fb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=192.168.1.67 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:1a:73:a8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Any help much appreciated :)

---

### Post by iPoi on 2008-07-14
Not sure if I can help as I haven't run inside XP, but I had a conflict with the ssb module on my 6715b.

Here is a link, but there may be one more suitable to your needs if you search! [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188621]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188621")

---

### Post by Quackcandle on 2008-07-14
> **iPoi said:**
> Not sure if I can help as I haven't run inside XP, but I had a conflict with the ssb module on my 6715b.

Here is a link, but there may be one more suitable to your needs if you search! [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188621]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188621")

Brilliant - thanks! Wi-fi connection now working after blacklisting ssb :D

---

