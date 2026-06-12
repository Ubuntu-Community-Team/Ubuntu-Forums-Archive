---
title: "Can't connect to WEP 64/128 Wifi Network / No Internet"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by aimhelix on 2008-08-24
Hi all. This is my first post in the Ubuntu forums.. after a long time I finally took a dive and sat down and installed it on my laptop. Everything went without a hitch during the installation but when I tried to get on the net, it was a no go :(

My computer is a Toshiba Satellite A205 S5800 -- the first problem was the drivers so I researched that and found that I had to use ndiswrapper and the Realtek Win98 R8187B drivers with an edited INF file. After the quick research/Ubuntu crash course, I got my wireless card detected, but still no net :(

This is pretty much my first time using Ubuntu so whatever commands I've used are stuff I've gotten from reading around so far:

```
john@lucas:~$ sudo lshw -C network
[sudo] password for john: 
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:99:89:db
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:95:f7:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.52+Realtek Semiconductor Corp. link=no multicast=yes wireless=IEEE 802.11g

---------------------------------------------------------------------------

john@lucas:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:99:89:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68602 (66.9 KB)  TX bytes:68602 (66.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:95:f7:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4677 (4.5 KB)

---------------------------------------------------------------------------

john@lucas:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:44:95:f7:da
Sending on   LPF/wlan0/00:16:44:95:f7:da
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

----------------------------------------------------------------------------



```

Each time I try to connect to my WEP through the 'Wireless Connections' icon on the top right, it asks for my WEP key.. I've tried both HEX, ASCII (what is LEAP?) but after a minute or so, the window comes back asking for it again - 

Does someone know what I might be doing wrong? I'm a total amateur to this so I'm hoping someone could kindly help me. Thanks guys.

---

