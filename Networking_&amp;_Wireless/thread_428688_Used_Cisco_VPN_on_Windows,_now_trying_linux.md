---
title: "Used Cisco VPN on Windows, now trying linux"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by z-vap on 2007-04-30
Hey fellows,

I used Cisco VPN on Windows XP Pro, now I'm trying linux and installed Ubuntu (6.10 I think)  Now I am attempting to get myself totally off of Windows, and use Linux.  

For my work, we connect via a Cisco VPN Client and use a Key Fob to validate ourselves into the network.  I assumed that I could use OpenVpn, due to "Transparent Tunneling > IPSec over TCP" requirements for my connections.

Truthfully I have no clue what I am doing.  I installed something, and now don't know if I needed it or not;  I don't know how to uninstall it if I don't need it. 

What can I use to connect to my work server, and how can i uninstall this package I installed?  :confused: 

Thanks

---

### Post by sdide on 2007-04-30
~# apt-get install vpnc

you need to know groupname, grouppassword, user and userpw and peer, then you just type

~# vpnc

---

