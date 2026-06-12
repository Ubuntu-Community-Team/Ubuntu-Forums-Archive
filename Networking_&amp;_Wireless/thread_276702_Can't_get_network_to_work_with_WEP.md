---
title: "Can't get network to work with WEP"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by walker15 on 2006-10-13
As the topic suggest, I have trouble connecting to my home network with WEP enabled. If I disable WEP on my hub, it connects without any problems. So far I've tried everything from adding open or restricted to /etc/network/interfaces, to installing and trying WIFI-Radar without any luck. Tried entering the WEP key in both hex- and ascii-format, without that making any difference. 

Oh, and I'm using Xubuntu (Dapper) and my wireless card is a Zyxel ZyAir B-100.

Thanks in advance!

---

### Post by meng on 2006-10-13
Have you tried dropping to terminal?
sudo iwconfig eth0 essid <essid name> key restricted <key in hex>

substitute eth0 for your interface

if you want to enter key in ascii, I believe it's the same except enter key as s:<key in ascii>

If not restricted, leave out the word restricted.

After this,
sudo dhclient eth0

---

### Post by walker15 on 2006-10-15
Hmm, that didn't seem to work :-? 

Tried entering in both hex and ascii, but that didn't make any difference.
This is what I got:
```
andy@GLaptop:~$ sudo iwconfig eth0 essid XXXX key XXXX-XXXX-XX
andy@GLaptop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:a0:c5:40:25:a7
Sending on   LPF/eth0/00:a0:c5:40:25:a7
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
Trying recorded lease 192.168.1.37
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```
Any other suggestions? Thanks for the help btw!

---

### Post by walker15 on 2006-10-15
Okay, I managed to get it solved now. The problem was that the wireless connection had the key index set to 1 (used "sudo iwlist key" to find out), and I use 3 on my network. I managed to solve it by resetting the password with "sudo iwconfig eth0 key off" and then reentering it as "sudo iwconfig eth0 key [3] S:XXXXX".

---

