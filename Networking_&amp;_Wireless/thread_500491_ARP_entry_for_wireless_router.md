---
title: "ARP entry for wireless router"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by tava0002 on 2007-07-13
My wireless on Xubuntu is working fine now but when the arp cache expires after a period of inactivity the arp table gets cleared and I lose my connection.  

My solution is to add a permanent arp entry for my router with arp -s x.x.x.x 00:00:00:00:00 where x.x.x.x is the routers ip address and 00:00:00:00:00 is the router MAC address.   

Is there a file in Linux that runs at boot time that can run this  command so I don't have to do it manually? In FreeBSD the file is /etc/rc.local, is it the same in Linux?

---

### Post by Mr. C. on 2007-07-14
How about :

/etc/sysconfig/network-scripts/ifup-post

This runs after the interface is brought up, which is more likely what you want.

MrC

---

