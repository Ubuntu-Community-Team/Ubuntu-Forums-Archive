---
title: "2NIC, 2IPs but one faster connection"
date: 2019-05-28
forum: Networking &amp; Wireless
---

### Post by lfaino on 2019-05-28
Dear All,
I have a question and I do not know if someone can help.

I work at the university and the institution limited internet speed at 10Mb per second. However, I got a new computer with two Network card and I can request two IPs.
I would like to test whether combining the two cards with two IPs, i can increase internet speed. I saw few examples in netplan examples but none of them can help me.

Can you someone help?

cheers
Luigi

---

### Post by CatKiller on 2019-05-28
It's called link bonding or link aggregation. You need a switch that supports it and to have it configured properly. I've never got it to work.

However, if the University has limited the bandwidth so that there's enough for everybody, taking more than your share seems selfish to me.

---

