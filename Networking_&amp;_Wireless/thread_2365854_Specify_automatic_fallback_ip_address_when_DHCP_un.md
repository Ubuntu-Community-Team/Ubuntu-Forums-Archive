---
title: "Specify automatic fallback ip address when DHCP unavailable?"
date: 2017-07-11
forum: Networking &amp; Wireless
---

### Post by desdan on 2017-07-11
I have created a product running ubuntu server. I would like to configure the initial network setting for DHCP. Some of my customers, however, put my device on a network without a DHCP service. Is there a way to specify a specific fallback address if there is no DHCP?  For example I would loke to specify that my unit gets the address of 192.168.1.93 if no DHCP assignment is made. Is this possible?  My customers generally cannot be asked to get a keyboard and monitor and edit the interfaces file.

---

### Post by TheFu on 2017-07-11
You can script anything.  Perhaps if the DHCP fails, copy in an interfaces file (be certain to check for the correct subnet to be used) and restart networking.  I would never assume a 192.168.1.x network. 192.168.0.x is more popularly and my ISP's routers gives out 10.1.10.x addresses while my network is on 172.22.x.x subnets.

---

