---
title: "Speedstream 4200 &amp; Dlink"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by Absolom on 2006-12-05
I am having the strangest problem... I recently switch ISPs from Shaw cable to Bell Sympatico.  My new acct is active I manually configured the modem giving it my username and password and I have no problem using the internet when modem connected directly to my laptop via the ethernet cable. The prob starts when I try adding the Dlink DI-604 router in there the laptop says it's connected.. I went into the DLINK control panel and adjusted WAN from Dynamic Ip to PPPoE  I set it to Dynamic PPPoE and put my username and password in there. hit apply and it restarted I went to Status tab disconnected and reconnected to be sure it was linked right... but for some reason when using the router every time I try to connect to any website I get sent to bell activation site that asks for username and password and says I'm activated but  still can't get to any other site.
Oh yes and when I switch Ubuntu dns changes in networking from the modem IP to the router IP 

Any ideas Hope I outlined things fully enough.](*,)

---

### Post by Absolom on 2006-12-05
After playing around with it alot I figured out the problem... it still had primary and secondary dns from my old dynamic IP addy connection when I switched to PPPoE it seems they were still there. I switched back to Dynamic IP then removed the 2 DNS entries and restarted the router then switched back to PPPoE  so now the 2 DNS entries were all 0s and now everything works fine

---

