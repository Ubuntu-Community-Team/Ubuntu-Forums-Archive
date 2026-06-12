---
title: "[SOLVED] Alternative default gateway WINXP"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by ayenack on 2008-10-03
Being a bit lazy here. But hopeful I might get a quick answer.
So.... does anyone know an equivalent to

**sudo route add default gw 192.168.1.2**

For Windows XP home that can be entered into XP's DOS command line or any other way to temporarily change the default gateway.

Thanks for any help.

ayenack.

---

### Post by warchief_ryan on 2008-10-04
its just as simple, just take a look at "route --help".

Here's the example from --help, which is pretty clear.
"route ADD 157.0.0.0 MASK 255.0.0.0  157.55.80.1 METRIC 3 IF 2"

route ADD (destination) (mask) (gateway) (metric) (Interface)


I don't often edit my xp box's routes but if this isn't temporary you can just delete the route with "route DELETE".

---

### Post by ayenack on 2008-10-04
Excellent. Thanks very much warchief_ryan. Pretty straight forward after all. Haven't installed the XP box yet but this should make life easier.

ayenack.

---

