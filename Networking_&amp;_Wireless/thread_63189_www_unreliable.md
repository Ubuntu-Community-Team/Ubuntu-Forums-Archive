---
title: "www unreliable"
date: 2005-09-07
forum: Networking &amp; Wireless
---

### Post by muszek on 2005-09-07
I'm not sure it's only www (kinda hard to measure other stuff).
Symptoms: 
-- some pages take forever to load (sometimes couple minutes, sometimes they won't load at all).  Slashdot does that often.
-- most pages (but not close to 100%) work OK.
-- it takes several seconds to connect to DNS servers.

I have a quality broadband and didn't have those problems for a long time (ever since I messed with IPv6 after having Ubuntu installed, but I can't remember what exactly I've done then).  
I think that problems started to appear after I upgraded the kernel (currently 2.6.10-5-k7).

Any hints?  Please, it drives me mad.  Sorry for not providing a lot of info, I'm quite new to linux and don't know much about networking.

---

### Post by mlomker on 2005-09-07
I've mostly seen this problem when one of the DNS servers was unreachable.  During the next 'outage' try going to a command line and type **ping [www.cnn.com](www.cnn.com)** or whatever, and see if it properly comes back with an IP address.  Look at the contents of /etc/resolv.conf and make sure that the listed name servers can be pinged.

---

