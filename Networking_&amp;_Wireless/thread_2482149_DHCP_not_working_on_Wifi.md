---
title: "DHCP not working on Wifi"
date: 2022-12-21
forum: Networking &amp; Wireless
---

### Post by neoraptor123 on 2022-12-21
Hello,

I am using Lubuntu 22.04 on a Minix Neo Z84U and have the following issue:
* I can see the list of all AP nearby and connect to my AP 
* I don't receive any IP address via DHCP from my router (network is fine as other devices are on it)
* If I set a fixed IP + DNS or the WLAN, I have internet connection


When using DHCP, I have no IP address in "ip a s wlan0".

I tried to change the dhcp provider to dhclient in the NetworManager.conf but still the same issue.

What can I do to debug and solve this and have the DHCP working ?
Thanks for your support !

Edit: here the requested debug info : 
* [https://paste.ubuntu.com/p/SPZZmkzjVd/](https://paste.ubuntu.com/p/SPZZmkzjVd/) 
* and here when the IP is set manually and internet connection is ok > [https://paste.ubuntu.com/p/MzJV7wvGXW/](https://paste.ubuntu.com/p/MzJV7wvGXW/)

---

