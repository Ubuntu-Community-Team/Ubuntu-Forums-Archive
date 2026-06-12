---
title: "Intel 2200 + networkmanager + weak network: disconnect not noticed"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by ernstblaauw on 2008-11-24
I have a Intel 2200 wireless card on my desktop, which runs Ubuntu 8.10. At home, I can connect to my WPA-PSK secured network without problems (the network strength is high, as I'm sitting almost next to the router).

On my university, I want to connect to the network. The network's security is WPA Enterprise with EAP-TTLS and PAP. There are a lot of access points with the same ESSID, to covert the whole university. The signal strength is not too well.

The problems are as follows: as soon as I am connected, I can surf on the internet. However, after some time (this can be seconds or more than 15 minutes) I'm disconnected (I cannot browse anymore), but networkmanager still shows a connection.

Does someone know how to 'inform' the networkmanager the connection is down?

BTW, I think this bug report is related: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293426](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293426)

---

### Post by vnarayan on 2009-04-26
i too have the same problem.
hardy 8.04 on a hp pavilion dv 6000 with a broadcom wireless card
i use ndiswrapper with the bcm 4328 driver.
works perfectly fine at home but disconnects after 5-15 minutes at university.
Is there a solution?

---

### Post by ernstblaauw on 2009-04-26
You have to search on Launchpad. Over there, a lot of bugs are reported related to network disconnects. For sure your problem has been reported earlier. I did not see a solution yet, other than use wpa_supplicant itself (without using NetworkManager) or downgrade NetworkManager to version 0.6.6.

---

