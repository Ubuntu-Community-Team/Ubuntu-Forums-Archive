---
title: "linksys wpc11 v3 on gutsy - solved"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by chrisb62 on 2007-11-04
basically, i was able to see and connect to the router, but couldnt load any websites.

after countless hours, and eventually deciding to just try anything and everything, i found this


add:

"blacklist hostap_cs" to the /etc/modprobe.d/blacklist file -  (without the quotes)

reboot, problem solved.

hopes this helps some people out.

---

