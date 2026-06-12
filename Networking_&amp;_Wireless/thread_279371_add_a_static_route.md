---
title: "add a static route"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by Andrea_44 on 2006-10-17
Hi,

I have 2 network interfaces and I am attempting to
select eth1 as my default gateway.

I try selecting it on the Network Setting screen (at the bottom),
but it always go back to empty (no interface is selected).

Thus, currently I have to default gateway set.
i.e when I do route -n the Gateway is 0.0.0.0

How do I add a default gateway manully into the routing table?
i.e.
route add -?? -??

I have tried reading the "man route", but I still can't figure it out
how to add a route properly.

Many Thanks,

Andrea

---

### Post by adwait on 2006-10-17
Try this:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html)

---

### Post by Andrea_44 on 2006-10-17
Thanks,that was very useful.

Cheers~
Andrea

---

