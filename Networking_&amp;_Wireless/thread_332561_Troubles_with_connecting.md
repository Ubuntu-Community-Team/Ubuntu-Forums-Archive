---
title: "Troubles with connecting"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by bluppy2 on 2007-01-06
Hi!

I'm using Dapper for a while and so far it's really working for me. But lately I'm experiencing a couple of issues with connecting with remote hosts with all kinds of programs.

The most obvious example in 'ping google.com'. Every first time when I try it it goes wrong, but when I try it a couple of times it will eventually connect:

```
bluppy2@tool:~$ ping google.com
connect: Resource temporarily unavailable
bluppy2@tool:~$ ping google.com
connect: Resource temporarily unavailable
bluppy2@tool:~$ ping google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=240 time=102 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=240 time=97.1 ms
etc.
```

Ping isn't the only program with these kinds of problems. Irssi, Apache2 and traceroute are experiencing similar issues. 
I use a 3Com network chip if I remember correctly. The DHCP lease goes well (no warnings or errors). I tried changing my resolv.conf, but that  didn't help anything. 

I hope someone can help! :)

---

### Post by bluppy2 on 2007-01-06
"/etc/init.d/ipsec stop" made everything work again. Since I don't use IPsec anyway so I removed it completely and all the problems are gone.

---

