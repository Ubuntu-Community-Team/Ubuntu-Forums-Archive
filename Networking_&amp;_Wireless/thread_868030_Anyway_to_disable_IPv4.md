---
title: "Anyway to disable IPv4?"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by g0tb00st on 2008-07-23
Yes, I said I'd like to disable IPv4, and NOT IPv6. I want my IPv6 host to query my local DNS over IPv6 for testing purposes. Any help would be appreciated.

Erik

---

### Post by broquea on 2008-07-23
If you could compile IPv4 as a loadable kernel module (the way IPv6 is) you could rmmod it. Otherwise you can edit resolv.conf to only have IPv6 addresses for nameservers to query against. That should make it so the host never talks over IPv4 to query DNS since it won't know of any.

---

### Post by silkstone on 2008-07-23
I don't know if this will work, but it's worth a try...

gksudo gedit /etc/modprobe.d/blacklist

Add "blacklist ipv4" to the end of the file.

---

### Post by ModelM on 2008-07-23
I think you can disable it by editing the /etc/modprobe.d/aliases file like this:

change:

alias net-pf-2 ipv4

to:

alias net-pf-2  off

---

### Post by AlexUhde on 2008-09-13
I tried the above but now I get a new Interface (eth0:avahi) which has am IPv4 address and spams the network with it. When I try to disable avahi I get an endless DHCPv4 request loop.

Can anybody point out to me what to do?

Regards,
AlexUhde

---

