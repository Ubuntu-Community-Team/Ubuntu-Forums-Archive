---
title: "ifconfig IP address"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by homebrewer on 2007-05-20
My wireless is always getting the same IP address. I tried to force wireless connection by issuing sudo ifconfig eth1 add 192.168.1.106. Now my wireless works, but the DHCP always gets 192.168.1.106 every time. How do I undo this.  I tried sudo ifconfig eth1 del add 192.168.1.106.  But, it still goes and gets 192.168.1.106.

---

### Post by tturrisi on 2007-05-20
If you use dhcp then the ip is assigned by the router, the address you get has nothing to do with the op sys dhcp service.  Try accessing the router control panel via the browser and view the dhcp clients table.  Delete the entrty for your comp & reboot the comp.  You will likely still get assigned the same ip address though because most home routers will assign dhcp addresses beginning w/ a certain number and go upwards as more clients connect.

---

