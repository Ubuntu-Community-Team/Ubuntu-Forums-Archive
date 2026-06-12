---
title: "ethtool has no effect"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by mr_mop on 2007-02-12
My network card seems to be stuck on 10baseT/Half, autoneg off.
I have tried many different ways to change the settings, but they never
seem to change.
sudo ethtool -s eth0 speed 100
sudo ethtool -s eth0 duplex half
sudo ethtool -s eth0 autoneg on etc etc

Is ethtool being overridden by some other mechanism?

---

### Post by mr_mop on 2007-10-26
Still got this problem after an upgrade to Gutsy.  Any ideas?

---

