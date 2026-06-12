---
title: "set up routing on localhost??"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by songshu on 2008-07-29
hi all,

Just wondering if this is possible and what would be the way to do this best.
The reason i'm asking is because i want to use TOR and am looking for an easy way to set this up, the current documentation speaks about configuring each individual program to route its traffic via SOCKS and this is a lot of manual work and i'm not to sure if all programs follow the config strictly.

So i was wondering on how to do this more easily and i have the following idea.

Instead of configuring each program to use something else then default, why not change the default and be done with it.

Lets say that instead of using ETH0 as the default we setup a DUMMY0 as the default and then use something like shorewall to route all incomming traffic on DUMMY0 to ETH0 or socks ?? via the ports for TOR.

Would this be a feasible approach when it comes to routing? would a virtual server on the same box be an answer if not?

thanks for reading this anyway.

---

