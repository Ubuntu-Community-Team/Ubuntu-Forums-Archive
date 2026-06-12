---
title: "Serial Modem Error"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by Atheist_Commie_Scum on 2008-02-11
I'm trying to get a serial modem to work on Ubuntu 7.10. It's a MultiTech MT56DSU2. Everything is plugged in and I went thorugh the steps I found in the online ppp tutorial. When I try to use pon I get this error:

/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'

Even though my modem device is set to ttyS0 in the network administration utility. /etc/ppp/peers/provider lists the modem device as /dev/modem. Can I change this file directly?

My guess is that it isn't detecting the modem? I used this same modem under freeBSD and was able to use tip and get a response from it, it also recognized it as a modem (though I couldn't get it connected). What should I do? Also, what is the linux equivalent of tip?

---

