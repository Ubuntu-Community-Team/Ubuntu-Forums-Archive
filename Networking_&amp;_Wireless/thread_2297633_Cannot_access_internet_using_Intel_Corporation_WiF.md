---
title: "Cannot access internet using Intel Corporation WiFi Link 5100 with D-Link DIR-615"
date: 2015-10-05
forum: Networking &amp; Wireless
---

### Post by benjitz on 2015-10-05
Hello!

I recently got a new laptop (Dell Latitude E4300), and inserted my existing hard drive with Ubuntu installation on it. Whereas the wifi worked fine on the previous laptop it was in, it is having issues with this. It sees networks fine, and can connect to my home router (D-Link DIR-615) with a good signal, but I can't seem to access the internet at all. It sends packets out but receives nothing back. The internet works using ethernet only. Also, the laptop can connect and use the internet on at least one other router using wifi too, that I have tried. Other wifi devices like my iPad can access the internet using the D-Link router using wifi fine too.

I am tempted to think it's a DNS issue, but I also cannot access the router settings on 192.168.0.1 using wifi either, which I would have thought was a DNS issues. I cannot see anything obvious that needs changing in the router settings. Here's a spattering of them for your perusal:

All of your Internet and network connection details are displayed on this page. The firmware version is also displayed here.

Firmware Version : 1.00VG ,  Tue 05 May 2009
LAN
MAC Address : 	 14:d6:4d:74:03:2e
IP Address : 	 192.168.0.1
Subnet Mask : 	 255.255.255.0
DHCP Server : 	 Enabled
Internet
MAC Address : 	 14:d6:4d:74:03:2f
Connection : 	 DHCP client 
 
IP Address : 	
 81.96.166.42
Subnet Mask : 	
 255.255.252.0
Default Gateway : 	
 81.96.164.1
DNS : 	
 194.168.4.100 194.168.8.100
Wireless 802.11n
SSID : 	 dlink
Channel : 	 6
Encryption : 	 Disabled

In addition to this, I have tried it with an external USB wifi adapter (Realtek 8192CU) but the issue remains the same, can connect to router, but no internet.

I attach the output from the wireless-info script and hope someone can help. It was run with the external wifi adapter unplugged (would prefer to use it with the internal, if possible). I've been at this for a week and it's driving me a bit crazy! Any suggestions? Many thanks in advance!

[ATTACH]264822[/ATTACH]

---

