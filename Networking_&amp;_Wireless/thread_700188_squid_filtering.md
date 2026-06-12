---
title: "squid filtering"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by John Deas on 2008-02-18
I would like to setup an Internet proxy that would work like some paying wifi access. The idea is that each user is given a login and a password. When they try to connect, they are asked for both. Unless they provide credentials, all the pages are redirected to this login page. I undertood that squid is capable of this. But, I also understood that as squid is an http proxy, and as I would like to open all ports, setting iptables is the way to go.

What I would like to do is to close ports via iptables until a credential is given via the squid interface, and then allow traffic redirection on all ports (at least the ones useful for the client software).

Is this hard to setup ?

The first problem I see is that squid might use a cookie to store credential, which the games, p2p and co won't have access to.

Thanks,

jd

---

