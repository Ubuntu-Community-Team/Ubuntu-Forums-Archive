---
title: "no wireless internet since upgrade to 8.04 (using WPA)"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by tom_a_sparks on 2008-07-01
I am not getting an IP address both using manual/static or DHCP

> tom@tom-desktop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0f:3d:39:ef:0f  
          inet addr:10.0.0.23  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12675293 (12.0 MB)  TX bytes:2308577 (2.2 MB)

sudo lshw -C network
>   *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:3d:39:ef:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+prisma02 driverversion=1.52+Conexant,04/06/2004, 1.00.1 link=no multicast=yes wireless=IEEE 802.11g


> tom@tom-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dickets"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:D2:70:71   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:8917-90BA-E60D-29A5-69EF-455B-CED7-F0DA-7F6D-98F0-6020-DF87-96A4-0038-465D-9293   Security mode:restricted
          Power Management:off
          Link Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



---

