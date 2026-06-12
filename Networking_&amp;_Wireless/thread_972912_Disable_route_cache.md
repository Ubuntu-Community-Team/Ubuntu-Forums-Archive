---
title: "Disable route cache"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by dokaspar on 2008-11-06
Hi,

Is there any way to disable the route cache in Ubuntu?

My system has a working equal-cost multipath (ECMP) setup,
in which I would like that new connections are always assigned
to a new interface, without a lookup in the route cache.

The problem is that because of old entries in the route cache,
only one of my interfaces is actually used for multiple
connections to the same destination.

In other words, I want that "ip route show cached" always
displays nothing at all.

Best regards,
Dominik

---

