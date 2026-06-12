---
title: "connected to router, but no internet"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by ubuntumatic on 2006-09-20
Hi, 
I have a broadcome 4306 wireless card (linksys WPC54G v1.2) installed on Dapper.
I've followed all the threads about this subject, successfully installing bcm43xx and gnome network manager.

When i start ubuntu, network manager is able to see all networks and to connect to the one i am entitled to use (via MAC filtering). 

The router is set to broadcast SSIDD and is using 802.11 b and g.
I can ping the router and connect to it no problem.

However, i can't surf the web at all (no problems on windows).

I already tried disabling IPV6 both in ubuntu and firefox, with no success.
The only hint I have is that through network-manager i see the IP address i'm using is 192.168.1.84, I don't know where it comes from.

what am i doing wrong? please help me, i just can't wait to leave windows forever!

---

### Post by miceagol on 2006-09-22
I have the same problem after upgrading to ndiswrapper 1.23. Wireless is up and running, I have been given an IP address, but there's no  Internet. The wireless settings are the same as before the upgrade.
 
Anyone?

---

### Post by alienseer23 on 2006-09-23
also the same issue here, I have wireless active with the bcm43xx method and I have an ip address, I can ping and be pinged, I can connect to the router, but no internet, hope someone sees this!!!! Help!!!

---

### Post by alienseer23 on 2006-09-23
try this kids, is your /etc/resolv.conf a zero byte file? is it empty? or is the DNS tab blank in your admin-network gui? If this is the case you need to find out what your dns servers' addresses are and enter them in, and the search domain, otherwise you will not be able to resolve names, and not search the net. Call your provider for the info if you don't know it. That worked for me. Good luck.

---

