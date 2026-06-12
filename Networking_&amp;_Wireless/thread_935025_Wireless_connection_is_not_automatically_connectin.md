---
title: "Wireless connection is not automatically connecting to wireless Access Point"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by ww711 on 2008-10-01
Having recently removed wicd, successfully. I have gone back to using the gnome network manager applet.

When I boot the laptop up and gets to desktop, it displays the broken  connectivity icon. 

To regain my connection i sudo and use '/etc/init.d/networking restart'
this successfully connects me to my wireless AP.

Ideally I would not want to do this every time. I know that a file has to be edited, which file would it be?

---

### Post by ww711 on 2008-10-02
lshw -C network gives me:
[I]
*-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: eth1
       version: 01
       serial: ************
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,12/17/2005, 4.10.4 ip=************ latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: ************
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5788-v3.26 latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:4b:d0:f6:56:20
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/I]

iwconfig gives me:[I]

eth1      IEEE 802.11g  ESSID:"******"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: ************   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]


Clearly, I can can detect the wireless AP, this only happens when I to  have issue the command of /etc/init.d/network restart' after loading into desktop. How to make the changes permanent so i do not have to keep loading that same command?

---

