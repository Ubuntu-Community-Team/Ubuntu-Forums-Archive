---
title: "How do i find the Lan IP address"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by GenDeath on 2009-10-19
In Damn Small Linux a Debian Based system im tying to create a LAN Web Host for transferring files locally

do i need to open any ports just for transferring files between ubuntu / DSL / Windows ?

It comes with the monkey server daemon installed which is a modded apache as far as i can tell

tyvm

---

### Post by sandyd on 2009-10-19
> **GenDeath said:**
> In Damn Small Linux a Debian Based system im tying to create a LAN Web Host for transferring files locally
 
do i need to open any ports just for transferring files between ubuntu / DSL / Windows ?
 
It comes with the monkey server daemon installed which is a modded apache as far as i can tell
 
tyvm
It should automatically open ports for you.
or rather, apache does.
 
for the network ip address,
```

iwconfig

```

---

### Post by GenDeath on 2009-10-19
My bad it was i needed to change the Virtual Box Connection Card to use the host interface now it works so thanks :D

Please close thread :D

---

