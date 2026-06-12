---
title: "lost wireless"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by tednugent on 2007-11-26
I had a laptop with ubuntu wireless worked great however due to neighbors borrowing too much bandwidthI was forced to password my linksys now I cant get ubuntu to even catch a signal I have tried averythin my pea brain can think of and still no internet if anyone has any ideas please let me know I put in the network password  even tried to configure it static it just doesnt even want to pick up a signal thanks

---

### Post by growingtedium on 2007-11-26
Try 
> 
iwlist ath0 scanning

and see if it is listed there.  You'll probably need to switch ath0 for whatever you're wireless interface is (find it using ifconfig - it's not lo or eth)  If the router is broadcasting that should at least 'see' it.  If the essid is hidden, look at the signal strength and channel to identify which one is yours.

---

