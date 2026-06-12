---
title: "Regenerating 70-persistent-net.rules"
date: 2016-10-13
forum: Networking &amp; Wireless
---

### Post by platypusclaw on 2016-10-13
so I've been doing research and its lead me to /etc/udev/rules.d and apparently there is supposed to be some sort of [COLOR=#000000]70-persistent-net.rules in this file mine is blank, I've turned my wifi on and off I've re-booted and still no files.[/COLOR]

[COLOR=#000000]My main point is I'm trying to find wlan0 bu it's not available when i try and do ifconfig.[/COLOR]

---

### Post by Hadaka on 2016-10-13
Hi, from ubuntu 15.10 on...and now 16.04 there no longer is a /etc/udev/rules.d/70-persistent-net.rules.
nor is there any longer wlan assingment name.
to see what your wireless assingment is please post the output of..
```
ifconfig
```
you should notice that your old eth0 is called something else also.
thanks.

---

