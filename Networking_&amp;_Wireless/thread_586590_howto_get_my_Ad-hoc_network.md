---
title: "howto get my Ad-hoc network"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by inckie-lap on 2007-10-22
How do i setup my adhoc network, i use a Windows XP machine as "server or gateway"

i can see the wireless network in network manager on ubuntu, and i can connect to it but, i doesn't get the right ip i wan't.

Because im sharing my internet connection from my XP machine to my laptop i need to set Ubuntu up with a static ip

ip: 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

howdo i set the wireless network card up with this?

---

### Post by mazen_skystar on 2008-05-07
please help
it is same my problem since 4 mounths

thanks

---

### Post by mazen_skystar on 2008-05-08
its happend:guitar:
mazen@mazen-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"maz"  Nickname:"maz"
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 32:7C:A0:15:CD:E6   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mazen@mazen-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:18:0f:b0:28  
          inet addr:100.50.0.50  Bcast:100.255.255.255  Mask:255.0.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0xf000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27252 (26.6 KB)  TX bytes:27252 (26.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:10:6f:12:c2  
          inet addr:192.168.0.45  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3511905 (3.3 MB)  TX bytes:412605 (402.9 KB)


but i m really i don't know how

---

### Post by moreal008 on 2008-06-26
In this case,can't use network manager.

this is a guide to using ad-hoc network

[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

---

