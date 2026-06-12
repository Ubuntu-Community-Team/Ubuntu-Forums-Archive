---
title: "Disabling IPv6 does not fix problems with Gaim"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by k1001001 on 2006-11-22
So I disabled IPv6 in this manner:
-Terminal
-sudo gedit /etc/modprobe.d/blacklist
And I added this line at the end of the blacklist file:
-blacklist ipv6

This got Firefox to work perfectly, but Gaim is still not working. 

I also tried option 1 on post 4 of [this]("http://www.ubuntuforums.org/showthread.php?t=78337") thread, but no luck with Gaim either. 

It works fine on this computer I'm using to type, which is connected to the same router. This is only a problem here at home and not at college. Any suggestions?

---

### Post by k1001001 on 2006-11-22
Fixed the problem. In addition to doing the other steps, I followed the "Editing the /etc/dhcp3/dhclient.conf" step at [this]("http://www.ubuntuforums.org/showthread.php?t=282034") thread.

If you do not know how to get your DNS addresses, go to your browser and type your router's IP address in the address line. My router's IP (and I think most are set up this way) is 192.168.0.1. From there, find a link relevant to the status of the router. Mine simply said "Status." There, it should list the router's 2 DNS addresses. The thread above also describes how to get OpenDNS addresses in case you cannot find this information, or it does not work.

Hope this helps for anyone with a similar problem.

---

### Post by Swivel on 2006-11-23
thanks mate it did :)

---

