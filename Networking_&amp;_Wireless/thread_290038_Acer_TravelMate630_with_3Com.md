---
title: "Acer TravelMate630 with 3Com"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by scoobyNZ on 2006-10-31
Hello, Any help appreciated. I have installed 6.06 and have everything going nicely except for the 3Com 3CRWE154G72 wireless card. From what I can make out with my limited experience the drivers are working alright, it just seems that the card is not turned on. How do I turn the card on, when I put the card in none of the lights come on. The card pug used to plug and play in XP without any other actions.

Please find my lshw and iwconfig below, any help appreciated

craig@craig-laptop:~$ sudo lshw -C network
Password:
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth0
       version: 10
       serial: 00:00:e2:92:a1:e1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.0.2 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:e0002000-e00020ff irq:10
  *-network DISABLED
       description: Wireless interface
       product: 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@02:00.0
       logical name: eth1
       version: 01
       serial: 00:30:b4:00:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 multicast=yes wireless=NOT READY!
       resources: iomemory:42000000-42001fff irq:11
craig@craig-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      NOT READY!  ESSID:"Get-Out"
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Cheers!

---

### Post by giannimesa on 2008-02-20
I have the same problem with the same 3Com wireless card, but with a Toshiba Satelite.
With Ubuntu 7.10

somebody know how do it work?

---

