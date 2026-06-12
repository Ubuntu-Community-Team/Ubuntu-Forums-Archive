---
title: "Adding 192.168.1.1 NAS To HOSTS File"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by swormuth on 2014-06-06
In order to get DejuDup automatic backups to work, I added the line "192.168.1.1 NAS" to my hosts file.  This is the same local IP address of my router, and I was wondering if the network guru's see any potential problems, security or otherwise, with doing this?

TIA

---

### Post by tgalati4 on 2014-06-06
If your router has the address 192.168.1.1 and is acting as a gateway, then that would be a problem.  Why can't you manually assign another address?  You have 255 to go.  After assigning a manual IP address, you typically need to reboot your router for the network tables to update.

---

### Post by swormuth on 2014-06-08
Don't see a way to assign a different IP.  By "NAS", I am referring to a USB drive attached directly to the routers USB port, which is managed by the router itself.  It seems to be working fine, but my main concern is whether there are any security risks from the outside world doing this...?

---

