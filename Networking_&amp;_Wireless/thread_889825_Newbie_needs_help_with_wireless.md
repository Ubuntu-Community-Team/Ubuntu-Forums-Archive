---
title: "Newbie needs help with wireless"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by chriswhiteoak on 2008-08-14
Hi, I have just installed Ubuntu for the first time, i'm new to anything linux but it all looks goood so far. Only thing is I'm having a lot of difficulty trying to work out how to connect to my wifi. I think it has something to do with enabling my wlan or a driver or something but i really don't have a clue, Ubunutu is scaring me!! lol.

While reading other threads trying to work it out i noticed people were posting these, so if any of this helps anbody:

chris@chris-ubuntu:~$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: wmaster0
       version: 00
       serial: 00:10:60:67:44:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:96:69:3b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=128 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s


chris@chris-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


chris@chris-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:d0:96:69:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4700 (4.5 KB)  TX bytes:4700 (4.5 KB)



If anyone can help me it would be much appreciated if you can give step by step instructions, as i have only been using linux for a day.

Many thanks

---

