---
title: "problems forwarding NTP through router"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by tr333 on 2007-12-07
I'm having problems forwarding NTP requests through my router to my server.
When I synchronise NTP on my desktop to the server using the LAN address (192.168.x.x) it works, but when I try to synchronise through the external address (mysite.dyndns.org) it fails.  Other people are able to synchronise NTP to my server using the external address.
It seems strange because other ports (HTTP/HTTPS) are not affected by this and I can access them from both LAN and external addresses.

On a side note, running "ntpdate -q serverlanip" and "ntpdate -q 0.au.pool.ntp.org" both succeed, but running "ntpdate -q mysite.dyndns.org" results in ntpdate crashing with a "bus error".

---

