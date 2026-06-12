---
title: "ksoftirqd/0 100% cpu - network problem"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by superbo8218 on 2008-02-10
hi

i have ubuntu 7.10 router with 3 interfaces. from time to time the cpu load goes high and top says that ksoftirqd/0 is using 70-100% of the cpu. it drops to 0 immediately after i plug off the cable from the interface that is conected to the internet. i had the same problem when the ruter was running on freebsd.

is it an attack from the internet or something else?

help please

MACEDONIA

---

### Post by superbo8218 on 2008-02-11
i found that this was attack from the net from random ip adresses and source ports 1024 and 3027 and destination port 22. it had about 40000 packets/sec.

any idea how to prevent such S*IT ??

---

