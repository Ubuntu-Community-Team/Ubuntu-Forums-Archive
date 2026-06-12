---
title: "Problems with network - Kubuntu 5.10"
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by Husio on 2005-11-18
Hi, 
I have problem with my Kubuntu-personal PC. 

Few days ago I have installed Ubuntu 5.10 on my server. I've configurate it, and install bind9. 
After adding new DNS on each computer, everything's goes fine. But not on my Kubuntu. It doesn't see network, only lan. Other computers (XP, Aurox-linux) runs with no problems.

Don't know what to do... :/

**Here is my server config:**
IP : 192.160.0.1
Mask : 255.255.255.0

------------------ rc.maskarada script --------------------------------

#!/bin/bash

# Pare regulek, zeby laptop dziala :)

iptables -I FORWARD -s 192.168.0.0/24 -j ACCEPT
iptables -I FORWARD -d 192.168.0.0/24 -j ACCEPT

iptables -I INPUT -s 192.168.0.0/24 -j ACCEPT
iptables -I INPUT -d 192.168.0.0/24 -j ACCEPT

iptables -t nat -I POSTROUTING -s 10.10.80.0/24 -j SNAT --to-source 195.117.213.100 

----------------------------------------------------------------------

**Other PCs:**
IP : 192.168.0.4/12
Mask : 255.255.255.0
DNS : 194.204.159.1 
         194.204.152.34

---

