---
title: "wireless disonnections"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by laro on 2007-10-24
Hi

I installed ubuntu 7.10
i have wirelss card - levelone 0301

when ubuntu turn on, it connect to the internet automatically
the signal strength is very good (87%)

but after few minutes it disconnect and i cant connect again (if I restart the computer it connect again... but few minutes after same problem)

*** with windows i dont have this problem at all ***

iwconfig:

lo no wireless extensions.

eth0 
no wireless extensions.

wmaster0 
no wireless extensions.

wlan0 
IEEE 802.11g ESSID:"linksys" 

Mode:Managed Frequency:2.452 GHz Access Point: 00:16:B6:E1:7F:44 

Retry min limit:7 RTS thrff Fragment thr=2346 B 
Encryption keyff

Link Signal level=-49 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 
Invalid misc:0 Missed beacon:0



ifconfig:

eth0 Link encap:Ethernet HWaddr 00:1A:4D:93:24:84 

UP BROADCAST MULTICAST MTU:1500 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0

TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 

RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:16 Base address:0xa000 

lo Link encap:Local Loopback 

inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1

RX packets:56 errors:0 dropped:0 overruns:0 frame:0
TX packets:56 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:0 
RX bytes:5094 (4.9 KB) TX bytes:5094 (4.9 KB)

wlan0 Link encap:Ethernet
HWaddr 00:11:6B:3C:94:3E 
inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0

inet6 addr: fe80::211:6bff:fe3c:943e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

RX packets:4377 errors:0 dropped:0 overruns:0 frame:0
TX packets:4193 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000 
RX bytes:2179449 (2.0 MB) TX bytes:518706 (506.5 KB)

wmaster0 Link encap:UNSPEC
HWaddr 00-11-6B-3C-94-3E-00-00-00-00-00-00-00-00-00-00 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)


the etc/network/interfaces file:
auto lo
iface lo inet loopback


what can i do to fix it ?

(i assume but not sure it is something with time limit... but how can i change or disable it )

---

### Post by Gen2ly on 2007-10-24
This is a [good site]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") to to learn what you need to do to manually internet connect.  

I had previously two instances where internet connections didn't hold.  One was when my wireless extensions needed to be tuned.  [See.]("http://madwifi.org/wiki/UserDocs/UsersGuide")

The other time was when a neighbor hacked my network. :)

  Good Luck.

---

