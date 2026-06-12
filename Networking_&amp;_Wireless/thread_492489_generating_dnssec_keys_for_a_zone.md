---
title: "generating dnssec keys for a zone"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by jmoe74 on 2007-07-04
I am trying to generate dnssec keys for my zone. When I type the command:

dnssec-keygen -a RSA -b 512 -n ZONE myzone.com

from my working named directory, it looks like the command is doing something, but it has been running for at least 30 min now. I am wondering if this should take this long or if I am doing something wrong.

---

### Post by kidders on 2007-07-05
Hi there,

You *may* be having a depleted entropy issue. By default, **dnssec-keygen** uses /dev/random as its source of random data for key generation. If, for some reason, demand outstrips supply, the process could appear to hang, while it waits for more numbers.

One solution might be to use /dev/**u**random instead. It's a "less random" (and hence easier to generate) source of random data.

---

