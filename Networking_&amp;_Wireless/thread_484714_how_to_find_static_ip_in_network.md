---
title: "how to find static ip in network"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by asyed25 on 2007-06-26
hi everybody,
I just want to know how to find systems using static ip addresses in a network
in my office there are six hundred systems,in which the ip's are configured automatically some people have set static ips due to which ip conflicts are occuring in our network.
can anybody please help me in resolving this issue

Thanks in advance
Ansari

---

### Post by PaulFr on 2007-06-26
[http://www.angryziber.com/ipscan/](http://www.angryziber.com/ipscan/) for Windows

---

### Post by spd106 on 2007-06-26
I can't think of a better way than to eliminate those still using dhcp, then run a network scanner such as nmap to find the others. 

Unless you have a pre-generated dhcp client list from the dhcp server, you could set off a packet capture by the dhcp server, then either wait for renewals, though you would be relying on a short lease expiration time or instead perhaps force them to renew somehow. I think there is an rfc about that, though I doubt it's widely supported.

Once you have a list of those using dhcp, use nmap or some other network scanner to find those that don't and capture their mac addresses, shouldn't be too hard to track them down then. Arping is another useful tool.

There's probably a tool out there that does all of this automatically.

---

