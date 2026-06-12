---
title: "Wireless Network troubles"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by Iwneferi on 2008-09-09
I have a brand new belkin wireless USB adapter. As far as I can tell I have installed the necessary drivers and whatnot. I have also gone through the Ubuntu documentation, and the sticky here to solve my problem; to no avail.

As far as I can tell I am able to connect to the router and even get an IP address, but I cannot ping [www.ubuntu.com](www.ubuntu.com). In the terminal when I type in iwconfig, I get the response:

lo     no wireless extensions.

eth0   no wireless extensions.

wlan2 IEEE 802.11g ESSID:"NETGEAR"

And a bunch of other stuff.

When I type in ifconfig, I'm given IP addresses for all three of the above. I can't find out what to do anywhere. I could really use some direction. 

Thanks in advance!

***

Apparently, it only sometimes connects to the router and gets an IP address. Sometimes it doesn't. This concerns me greatly.

---

### Post by superprash2003 on 2008-09-09
are you getting an ip of the form 169.x.x.x or of the form 192.168.x.x?

---

### Post by mark5771 on 2008-09-13
this helped me -

[http://forums.remote-exploit.org/showthread.php?t=14241](http://forums.remote-exploit.org/showthread.php?t=14241)

I have Belkin D7F-7050 ver#4

After I installed the updated drivers, just plug & play!

M

---

### Post by mark5771 on 2008-09-13
correction - to the above - I have the F5D7050 ver#4

---

