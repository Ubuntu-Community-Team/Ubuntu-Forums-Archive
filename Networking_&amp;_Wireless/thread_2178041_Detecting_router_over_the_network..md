---
title: "Detecting router over the network."
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by akshay-sulakhe on 2013-10-01
Hey guys, So my ISP does not allow me to use a router, still i was using it for over a year by cloning my MAC. But since last 3 days, they say you are using 4 different MAC addresses instead of one. How  can i circumvent this problem? I tried resetting the router and cloning mac again, doesnt work. Kindly let me know. Ty.

---

### Post by akshay-sulakhe on 2013-10-01
I have a router from Hama, don't know the model number though.

---

### Post by houstonbofh on 2013-10-01
They may be doing DPI and finding the MAC addresses in the NAT tags.  The only fix is to build a Linux server that does http proxying.  That will also limit you to web traffic only.

Alternatively, if you set up the server as a router and terminated at a VPN, or used something like m0n0wall and terminetd at an IPv6 VPN, they would see nothing.

---

### Post by QIII on 2013-10-01
You need to contact your ISP to resolve this.  The Forums are not an appropriate place to discuss circumventing the restrictions your ISP places on your service.

Thread closed.

---

