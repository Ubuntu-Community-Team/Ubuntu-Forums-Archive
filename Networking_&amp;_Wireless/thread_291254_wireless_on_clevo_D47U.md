---
title: "wireless on clevo D47U"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by Vinger on 2006-11-02
Hello,

I have a laptop Clevo D47U
There is a wireless card on board. (USB)

This is the output of the folowing commands:
> 
koen@koen-laptop:~$ dmesg | grep -i eth
[17179590.780000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17179590.780000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17179590.780000] eth0: RTL8169 at 0xf89d6000, 00:90:f5:26:49:c1, IRQ 225
[17179592.196000] r8169: eth0: link down
[17179592.500000] r8169: eth0: link up
[17179597.504000] Driver 'sd' needs updating - please use bus_type methods
[17179607.772000] eth0: no IPv6 routers present

koen@koen-laptop:~$ lsusb
Bus 004 Device 004: ID 07ca:e820 AVerMedia Technologies, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 07c4:a600 Datafab Systems, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0967:0204 Acer (??) WarpLink 802.11b Adapter
Bus 002 Device 001: ID 0000:0000


What can i do to install the card to use my wireless network with my Kubuntu install?

I allready found this page, which isn't very good...
[http://linux-laptop.net/hosted/clevo-D40EV-Ubuntu-6.06-LTS.html](http://linux-laptop.net/hosted/clevo-D40EV-Ubuntu-6.06-LTS.html)

thanks in advance

---

### Post by Vinger on 2006-11-15
No-one an idea?

---

