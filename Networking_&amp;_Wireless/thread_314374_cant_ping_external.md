---
title: "cant ping external"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by mr tim esquire on 2006-12-07
I can ping the router fine (192.168.1.1)
but cannot ping [www.google.com](www.google.com) or [www.ebay.com](www.ebay.com)
firefox dosnt work

I have a dual boot system, and when i switch to XP the internet is fine.
Router is linksys BEFSR81

any seggestions?
thanks :)
tim

---

### Post by meng on 2006-12-07
Is this a wireless connection? Have you tried:
sudo dhclient eth0
(or whatever the id of your interface is)

---

### Post by mr tim esquire on 2006-12-07
i have tried manual ip cofigs and dchp or whatever it is in the network settings but neither work, this is on eth0 btw

---

### Post by meng on 2006-12-07
Oh okay, I'm out of ideas then. I guess you could post your /etc/resolv.conf

---

