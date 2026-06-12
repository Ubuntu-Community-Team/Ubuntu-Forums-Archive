---
title: "Active Routes"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by danharper on 2008-11-13
I have a problem that when my server is rebooted or I restart the network cards I have to re add my active routes manually(via webmin). How do I add these routes so that they are persistant after reboot etc.

Cheers Dan

---

### Post by iponeverything on 2008-11-13
create /etc/network/if-up.d/static-routes and make it executable. 


For example it might look like this:


#!/bin/sh
/sbin/route add -net 172.16.0.0 netmask 255.255.0.0 gw 172.16.0.1
/sbin/route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.0.0.1

---

### Post by danharper on 2008-11-13
What do I do to make it executable?

cheers dan

---

### Post by iponeverything on 2008-11-13
sudo chmod 755 /etc/network/if-up.d/static-routes

---

