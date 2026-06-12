---
title: "Why are both wired and wireless interfaces created?"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by shochatd on 2014-04-25
When I either restart my laptop and then log in, or wake up from suspend, with an ethernet cable connected, I first see the icon in the network indicator for the wired network, then the usual "hunting for wireless" icon and then it says it has connected to my wireless network. The ifconfig -a command confirms that I do indeed now have two active network interfaces, one wired (eth0) and one wireless (wlan0), each with its own IP address. The output from the route -n command seems to imply that it is using eth0 to get to the default gateway, which seems fortunate. So my question is, why is it bothering with wireless after it has already connected successfully with the wired interface? This is with 14.04, on a System 76 Lemur Ultra. I could be wrong, but I don't think it did this in 13.10.

---

