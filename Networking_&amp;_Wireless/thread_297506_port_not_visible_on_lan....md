---
title: "port not visible on lan..."
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by DonKyot on 2006-11-11
Hi,
Please stop me going mad.

I'm trying to get remote access to mysql server just over my LAN.
The thing is running and accessible via localhost... but not visible via 'machinename'](*,) 
Either from the same box or another.

I have done nothing with iptables (--list shows all ACCEPT) or any other firewall.
I'm on Edgy - and have made very few changes to the standard installation.
There's nothing particular with the router.
apachy/ port 80 works
ping/traceroute etc work

it's not (yet) a mysql problem because
telnet localhost 3306  ; works
telnet 192.168.1.x 3306; gives connection refused.

any ideas most welcome.
thanks.

---

### Post by emdeem on 2006-11-11
Have you commented out skip-networking in /etc/mysql/mysql.cnf?

---

### Post by DonKyot on 2006-11-11
> **emdeem said:**
> Have you commented out skip-networking in /etc/mysql/mysql.cnf?
I did...

but I just found that bind-address appears *twice* in the default file :mad: 
I only changed the first apearance - the second was off the bottom of the editor.

I knew it couldn't be hard... and now it works.
But I'll leave the thread in case someone else has the same problem.


thanks :)

---

