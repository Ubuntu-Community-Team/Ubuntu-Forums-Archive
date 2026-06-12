---
title: "Router-internet connection Problems"
date: 2005-11-19
forum: Networking &amp; Wireless
---

### Post by onejoy on 2005-11-19
I've got a PC and laptop Routed together.  I just recently installed Ubuntu onto the laptop.  Whenever both computers are connected I get ridiculously slow speeds, and I'm on a broadband connection.  I don't think it has anything to do with linux, but I can't get any good speed with both computers connected through my router...

Please help.

---

### Post by rjwood on 2005-11-19
I would try turning the power off for a minute or 2 and then try again.

---

### Post by greenway on 2005-11-20
Slow network speeds are often caused by collisions on the network, however when using only two computers, this would be very strange. You could use "ifconfig" to look for error's and/or dropped packets on your LAN or you can use "ethtool -S <NIC>" for a more detailed error report. If you need more help, post the results.

---

