---
title: "Name Server Lookup failing in 17.04"
date: 2017-05-16
forum: Networking &amp; Wireless
---

### Post by Joe Momma on 2017-05-16
I recently updated from 16.04 LTS (to 16.10 and then immediately) to 17.04.  Everything seems fine, but I can no longer access computers on my network by name.  I am also getting a lot of "Input/Output" errors when I try to access an NFS server on my network.  Does anyone have any idea why?  Everything worked fine in 16.04.

If I do an nslookup by ip, it seems to know the name of the machine, but if I look it up by name, it cannot find it.  I should note that other machines on this network have no trouble resolving these same computer names.

> joe@joe-Ubuntu:~$ nslookup 192.168.1.2
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
2.1.168.192.in-addr.arpa	name = PiHole.

Authoritative answers can be found from:


> joe@joe-Ubuntu:~$ nslookup PiHole
Server:		127.0.0.53
Address:	127.0.0.53#53

** server can't find PiHole: SERVFAIL



Thank you for any help you can provide.

---

