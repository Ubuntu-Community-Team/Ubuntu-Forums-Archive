---
title: "&quot;PAP Authentication Failed&quot;"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by DalianDragon on 2007-09-20
Hey, 

I've just installed "ubuntu" today and am trying to connect to the internet with it so that i can get online and find out how to work with the REST of ubuntu.

Anyway... i used "sudo pppoeconf" to setup my internet connection, which is adsl through a router using PPPoE.  However, when i try to connect, I get a:

"PAP Authentication Failed" message.  

What does that mean?  How do I fix it? 


Thanx.

---

### Post by DalianDragon on 2007-09-20
when i try "pon dsl-provider", it doesn't let me get online...
so, i try "dsl log" and i get this:

Sep 20 23:34:35 eric-desktop pppd[4133]: Connection terminated.
Sep 20 23:34:35 eric-desktop pppd[4133]: Exit.
Sep 20 23:40:42 eric-desktop pppd[5751]: Plugin rp-pppoe.so loaded.
Sep 20 23:40:42 eric-desktop pppd[5753]: pppd 2.4.4 started by eric, uid 1000
Sep 20 23:40:45 eric-desktop pppd[5753]: PPP session is 1489
Sep 20 23:40:45 eric-desktop pppd[5753]: Using interface ppp0
Sep 20 23:40:45 eric-desktop pppd[5753]: Connect: ppp0 <--> eth0
Sep 20 23:40:45 eric-desktop pppd[5753]: PAP authentication failed
Sep 20 23:40:51 eric-desktop pppd[5753]: Connection terminated.
Sep 20 23:40:51 eric-desktop pppd[5753]: Modem hangup

---

