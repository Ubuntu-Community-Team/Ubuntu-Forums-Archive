---
title: "Internet dropping out with bittorrent"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by adredwood on 2011-05-08
Hi there 

I'm using 11.04 on my HP mini notebook, having recently upgraded (through software updates) to this version. On my previous system, I had no problems with internet; after upgrading, it seems to drop out every time I open up a torrent program. It will work well for 5 or 10 minutes then I have nothing - browser stops working, torrent all at 0.00 kb/s. I'm using transmission by default, have tried using Qtransmission but had the same result. 

Anyone having similar problems? Any ideas? 

Thanks all -

Andy (:

---

### Post by papibe on 2011-05-08
When that happens, you loose the Internet connection for all computers in your LAN/Home?

Do you recover your connection if you restart?

Regards.

---

### Post by matthewbpt on 2011-05-08
The only time I have experienced this is with a crappy router. Anytime it would get more than about 200 connections (pretty normal when using bittorent) the router would crash so all computers connected to it would lose their internet connection until it was restarted. Try changing in the torrent program preferences the maximum number of connections to 100. If this solves the problem then either google your router model and find out if there's a workaround for it, or better idea, start shopping for a new router. The one I had which cause this problem was a D-Link router.

EDIT: Also disabling DHT and peer exchange in the torrent program alleviated the problem somewhat as well, try that.

---

### Post by diablo75 on 2011-05-09
Crappy Linksys router did this to me.  If you do go shopping for a replacement try to find one that you can load an open-source firmware, like dd-wrt, on to.  I have a linksys running dd-wrt on it and it has NEVER crashed, no matter what I do with it.

---

### Post by robgraves on 2011-05-09
> **matthewbpt said:**
> The only time I have experienced this is with a crappy router. Anytime it would get more than about 200 connections (pretty normal when using bittorent) the router would crash so all computers connected to it would lose their internet connection until it was restarted. Try changing in the torrent program preferences the maximum number of connections to 100. If this solves the problem then either google your router model and find out if there's a workaround for it, or better idea, start shopping for a new router. The one I had which cause this problem was a D-Link router.

EDIT: Also disabling DHT and peer exchange in the torrent program alleviated the problem somewhat as well, try that.

actually i have this same issue sometimes, is this the only possible cause, because i didn't have this issue when i was using 10.10, but seem to be having it with 11.04

---

### Post by Grenage on 2011-05-09
It is by _far_ the most common cause.  If you don't want to buy a new router, then reducing the number of per-torrent connections will help; 20-40, with an active queue of 2 would probably stop choking.

The problem is generally most prevalent when NAT is used (99% of home cases), and even more so when multiple machines/users are using the connection.

---

### Post by adredwood on 2011-05-09
Hey guys, thanks for the responses.

I tried lowering the connections per torrent and so far it seems to be holding up - at least it's lasted 10 mins, and that's far more than it's been giving me recently. 

Will let you know if anything changes, good luck to those still having the problem.

A (:

---

### Post by adredwood on 2011-05-09
Oh - also disabled DHT as suggested; 14 minutes and counting...

---

