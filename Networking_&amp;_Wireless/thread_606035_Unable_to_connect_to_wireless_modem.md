---
title: "Unable to connect to wireless modem"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by darrentownsend on 2007-11-07
I am new to Ubuntu (feisty) and having problems trying to get my wireless card to connect to my modem. I am using a Compaq Presario 2500 PC with a Belkin F5D7011 wireless card. Modem is a BT Voyager 2110 ADSL Wireless Modem. I can connect to the internet fine with an ethernet cable but just cant seem to get the wireless connection to work. I can see the wireless connection listed in system-admin-network and it seems to be configured ok. Can anyone please help ? Below I have listed the output from my 1) "iwconfig", 2) "ifconfig" and 3) "route" commands.
darren@darren-laptop:~$ sudo iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:"v" Nickname:"Broadcom 4318"
Mode:Managed Access Point: Invalid
RTS thrff Fragment thrff
Encryption key:367A-3837-6335-3861-716E-3677-36 Security modepen
Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

darren@darren-laptop:~$ sudo ifconfig
eth0 Link encap:Ethernet HWaddr 00:0D:9D:5F:00:23
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:767 errors:0 dropped:0 overruns:0 frame:0
TX packets:789 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:699599 (683.2 KiB) TX bytes:134437 (131.2 KiB)
Interrupt:10 Base address:0x8000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:14 errors:0 dropped:0 overruns:0 frame:0
TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:972 (972.0 b) TX bytes:972 (972.0 b)

darren@darren-laptop:~$ sudo route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
darren@darren-laptop:~$

Thanking you in advance

---

