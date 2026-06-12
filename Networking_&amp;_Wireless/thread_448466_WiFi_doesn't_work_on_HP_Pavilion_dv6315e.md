---
title: "WiFi doesn't work on HP Pavilion dv6315e"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by GoodSoft on 2007-05-19
I have installed Ubuntu 7.04 on this laptop.
Most things worked "out-of-box", except wireless network.
The card is detected, access point is found, even DHCP queries are sent and replies are received. And that's all. I cannot ping neither access point, nor other computers in network.
Accidentally, network appeared for about two minutes and I could ping AP and even get out to the Internet, but after that it again disappeared.
Does anybody know, what sort of problem could it be?

**Technical information**

iwconfig:
```
goodsoft@lappy:~$ iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:"GoodSoft"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0E:2E:A1:CE:05   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=91/100  Signal level=-41 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

goodsoft@lappy:~$ 

```

ifconfig:
```
goodsoft@lappy:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:1A:73:38:5D:16  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe38:5d16/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31609 (30.8 KiB)  TX bytes:57746 (56.3 KiB)
          Interrupt:255 Base address:0x8000 

goodsoft@lappy:~$

```

dhcp:
```
goodsoft@lappy:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1a:73:38:5d:16
Sending on   LPF/eth1/00:1a:73:38:5d:16
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.3 -- renewal in 346895 seconds.
goodsoft@lappy:~$ 

```

route:
```
goodsoft@lappy:~$ route
&#1058;&#1072;&#1073;&#1083;&#1080;&#1094;&#1072; &#1084;&#1072;&#1088;&#1096;&#1091;&#1090;&#1080;&#1079;&#1072;&#1094;&#1080;&#1080; &#1103;&#1076;&#1088;&#1072; &#1087;&#1088;&#1086;&#1090;&#1086;&#1082;&#1086;&#1083;&#1072; IP
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
goodsoft@lappy:~$ 

```

pinging AP:
```
goodsoft@lappy:~$ ping 192.168.2.1 
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.3 icmp_seq=2 Destination Host Unreachable
From 192.168.2.3 icmp_seq=3 Destination Host Unreachable
From 192.168.2.3 icmp_seq=4 Destination Host Unreachable

```


**Update:** It again started working. There were huge packet losses (~80%) for some time, but now it again works stable, though pings are enormous (>100ms), even if I sit near AP.
And speed is horrible too, no more than 40 KB/s in local network

---

