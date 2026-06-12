---
title: "how to throttle bandwidth on a shared Internet connection"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by lavezarez on 2010-03-31
How do I control bandwidth of each computer using a shared Internet connection, so that even if one of the computers is downloading a video in YouTube, I could still get a decent bandwidth in the other computers?

Here's my setup at home:
Xubuntu 9.10 - connected to a Huawei USB modem for the Internet, and eth0 wired connection to the switch. eth0 IPv4 settings is **shared to other computers**

Two computers, one Windows 7 and another Ubuntu 9.10 connected to the LAN and both using the Xubuntu as the gateway.

Thanks for your help, guys!

---

### Post by gabi83tm on 2011-10-12
I would also like to know this.

---

### Post by Mark Phelps on 2011-10-12
The most likely reason that the original post sat unanswered for so long is simple -- you basically can't do this.

There are advanced Quality of Service (QoS) options on some routers, and in the DD-WRT open source software available for some routers, that will allow you to throttle bandwidth based on the TYPE of connecting being used.

But, as far as I know, none of them allow throttling based on the IP address, or Mac Address, of the networking client PC.

---

