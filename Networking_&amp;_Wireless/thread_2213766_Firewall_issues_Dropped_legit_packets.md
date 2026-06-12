---
title: "Firewall issues: Dropped legit packets"
date: 2014-03-28
forum: Networking &amp; Wireless
---

### Post by sgofferj on 2014-03-28
Hi,

I have an issue with conntrack generally seeming over-picky. I see tons of legit  packets ending up it the inet2fw cleanup rule, mostly RSTs and other  "last packets" from services likes DNS and such. It seems, conntrack has  a rather low timeout or otherwise simply loses track of the connection.

The firewall is an Ubuntu Server 12.04 LTS guest on an Opensuse 12.3 host. I don't see this kind of behavior with Opensuse.

Any way to fix that?

-S

---

### Post by sgofferj on 2014-04-02
Bump

---

