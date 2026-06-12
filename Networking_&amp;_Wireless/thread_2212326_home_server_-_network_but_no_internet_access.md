---
title: "home server - network but no internet access"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by timo2 on 2014-03-20
Dear Ubuntu users,

I'm using a home server with Ubuntu which is running Samba, XBMC and some additional
services.

I'd like to block every internet access by servers configuration but it
has to be reachable by LAN and _**maybe **_1 single external IP address.

How can I realize something like this? Maybe by iptables?

Kind regards & thanks :-)

---

### Post by TheFu on 2014-03-21
Yes, through iptables - or use any of the dozen interfaces to it like ufw, gufw, firestarter, ...

But if you block internet access, how will the machine get patched?

---

