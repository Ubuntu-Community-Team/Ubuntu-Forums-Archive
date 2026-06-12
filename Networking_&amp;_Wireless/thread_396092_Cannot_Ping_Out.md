---
title: "Cannot Ping Out"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by JengaBlocks on 2007-03-29
Just installed Xubuntu and got a wireless card up and running. I can ping within my local intranet but am having problems pinging out (like google.com). I placed in /etc/resolve/conf:

nameserver xx.xx.xx.xx
nameserver yy.yy.yy.yy

which are my ISPs DNS servers

When I ping,  I get:
ping: unknown host [www.google.com](www.google.com)

Any ideas?

---

### Post by Jussi Kukkonen on 2007-03-29
Further debugging: Try to ping an outside address by ip. Also ping the nameserver.

It's *resolv.conf* BTW, was that just a typo?

---

### Post by JengaBlocks on 2007-03-29
> **Jussi Kukkonen said:**
> Further debugging: Try to ping an outside address by ip. Also ping the nameserver.

It's *resolv.conf* BTW, was that just a typo?

Yeah it was a typo... I can ping inside the intranet with local IP addresses but not outside (I mentioned in first post I did google.com and it didn't work).

---

### Post by JengaBlocks on 2007-03-29
Solved it... needed to route to the gateway

---

