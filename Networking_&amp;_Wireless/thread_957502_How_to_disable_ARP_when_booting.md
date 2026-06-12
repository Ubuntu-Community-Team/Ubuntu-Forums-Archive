---
title: "How to disable ARP when booting"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by arrowheart on 2008-10-24
I want to disable ARP automatically (booting). How can I make it? Which configuration file should I change?

Thanks

---

### Post by bab1 on 2008-10-24
I believe what you want is part of: ```
ifconfig
``` See the man pages.  Specifically```
 [-]arp Enable or disable the use of the ARP protocol on this interface.

```

---

### Post by arrowheart on 2008-10-24
Thanks. Can I configure the system and disable arp and load static arp table just when booting, or I have to run some scripts?

Thanks

---

### Post by bab1 on 2008-10-24
Dunno...

We would need know what you are trying to achive (or prevent).  There are other methods of stopping ARP B'cast.  What are you trying to do?  Are you working with a cluster or is it VM in any why?

Here is another idea: [http://kb.linuxvirtualserver.org/wiki/Using_arp_announce/arp_ignore_to_disable_ARP]("http://kb.linuxvirtualserver.org/wiki/Using_arp_announce/arp_ignore_to_disable_ARP")

---

### Post by arrowheart on 2008-10-25
I just want to disable ARP and have a number of computers load a static ARP taable on booting.

Thanks a lot!

---

