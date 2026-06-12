---
title: "can't ping from dapper, but I can ping the machine"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by the_dark_light on 2008-04-09
A problem I'm encountering on a fresh install of dapper (Server install)

I can't ping any other machines on my LAN but they can ping the machine in question.  There seems to be no reason why this should be the case.

The network interface is the onboard LAN on an Asus P4C800 mainboard.  I've used this board successfully with several linux distros before, so I doubt it's something wrong with the interface.

Has anybody encountered this problem with 6.06 before?

---

### Post by Iowan on 2008-04-09
Got a firewall installed?

---

### Post by the_dark_light on 2008-04-10
iptables is accessible through /sbin/ but there are no entries in /etc/inet.d/

I'm not sure if it's running.  Are there any other firewalls installed by default?

---

### Post by the_dark_light on 2008-04-11
> **Iowan said:**
> Got a firewall installed?

You were right, the firewall was causing the problem.  I erased iptables and now I can access other hosts (though with no security)

It was strange that I couldn't find a config file in /etc (either that or I've been using Fedora way too long)

---

