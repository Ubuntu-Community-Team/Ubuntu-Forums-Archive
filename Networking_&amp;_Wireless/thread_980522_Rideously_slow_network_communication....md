---
title: "Rideously slow network communication..."
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by StrangeWill on 2008-11-12
Currently processing 4.2 GB of info over my network at 36kb/s

Whoa, Ubuntu had this problem too (desktop) before I switched to Xubuntu, obviously this is some problem with the network core of Ubuntu itself, this is over my wireless card, but should be nowheres near this slow (much quicker in Windows)...

Any ideas on configuration tweaks or anything? I've seen threads on this but no solutions... Are Ubuntu developers really turning a blind eye from a massive bug in their system?


Mind you this is a intranet setup, I shouldn't need to worry about DNS (pure IP transfer), IPV6 (network only supports V4), or any other nonsense mentioned in the other threads. It's just terribly slow.


Runs nice and fast while wired, but 37kb/s wireless is way too slow.

---

### Post by StrangeWill on 2008-11-13
Bump, this is a widespread problem and no one has a clue?

---

### Post by StrangeWill on 2008-11-13
Also if this helps, I have an:
MSI Wireless 11G CardBus CB54G2


iwconfig shows wlan0 set at 1mb/s, cannot manually change it (command goes through but still reports 1 Mb/s), any ideas?

---

### Post by dmizer on 2008-11-13
You have a bug reported here: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/190515](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/190515)

---

