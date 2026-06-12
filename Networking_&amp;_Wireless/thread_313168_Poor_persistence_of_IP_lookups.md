---
title: "Poor persistence of IP lookups"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by frisket on 2006-12-05
Is there a setting where I can lengthen the time that an IP address is cached for (assuming they get cached somewhere).

Example: in Firefox, I type a search in the Google box in the icon bar. Firefox looks up the IP address of [www.google.com](www.google.com) through my ISP in the normal way, gets redirected to [www.google.ie](www.google.ie), which it looks up, and then gives me the results. Two minutes later I search for something else, and off it goes to my ISP's DNS again to look up [www.google.com](www.google.com). 

All applications do this, and it makes for delays, especially with something like Hotmail, which redirects you from site to site to site. 

Are IP addresses cached, and if so, where? Or is it application-dependent? And can the persistence be lengthened (ie from 2 minutes to something sensible like 2 months)? Or is the time-to-live exclusively determined by my ISP's DNS?

Of course I could add them to /etc/hosts, but this really ought to be addressed at the operating system level.

---

