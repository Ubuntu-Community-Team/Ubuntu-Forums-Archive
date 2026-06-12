---
title: "UFW kills access to share"
date: 2018-05-03
forum: Networking &amp; Wireless
---

### Post by somethingdumb on 2018-05-03
Help! Using UFW to kill all network traffic other than my VPN + local network - 1194 UDP allowed for VPN to reconnect by itself in case of failure.
This setup (rules below) works GREAT for a while, then kills my Samba share, and I have to disable UFW, mount the share, and re-enable it. It then works for another week or so.
Ideas?

Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing), disabled (routed)
New profiles: skip
 
To                         Action      From
--                         ------      ----
192.168.***.***             ALLOW IN    Anywhere                 
192.168.***.0/24            ALLOW IN    Anywhere                 
Anywhere                   ALLOW IN    192.168.***.***
 
1194/udp                   ALLOW OUT   Anywhere                  
Anywhere                   ALLOW OUT   Anywhere on tun0         
1194/udp (v6)              ALLOW OUT   Anywhere (v6)            
Anywhere (v6)              ALLOW OUT   Anywhere (v6) on tun0

---

