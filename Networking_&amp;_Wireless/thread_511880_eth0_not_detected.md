---
title: "eth0 not detected"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by cripperz on 2007-07-28
Hi guys,

is there anyways to detect the lan card back. I previously remove the old lan card and put in a new lan card. now im wondering how to purge the os to detect this new lan card. using ubuntu 6.06 server ... 

pls help

thanks in adv

---

### Post by netztier on 2007-07-28
> **cripperz said:**
> Hi guys,

is there anyways to detect the lan card back. I previously remove the old lan card and put in a new lan card. now im wondering how to purge the os to detect this new lan card. using ubuntu 6.06 server ... 


Probably, your old card had an entry in /etc/iftab that assigned it's MAC address to eth0.
The new card now has a different MAC address and therefore is assigned eth1 (probably, might also be some other number).

However, your /etc/network/interfaces has no configuration for a card called eth1 or eth2.

Solution: Remove or correct (with the new MAC address) the eth0-line in in /etc/iftab, so your new nic can automatically become eth0 (and have a configuration entry in /etc/network/interfaces again).

best regards

Marc

---

