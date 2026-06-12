---
title: "Computer won't route IPv6"
date: 2015-11-19
forum: Networking &amp; Wireless
---

### Post by ocwo92 on 2015-11-19
I'm trying to setup a server on our LAN as an IPv6 router. The LAN already has IPv6 connectivity via an IPv6 gateway/router. The server provides several services over IPv6 that the clients use happily, so as long as I use the IPv6 router, everything works perfectly.

However, I want the server to also act as a router, too, for various reasons. From what I can gather online, it's a simple question of enabling IPv6 forwarding, and it is currently enabled:

```
$ cat /proc/sys/net/ipv6/conf/p4p1/forwarding 
1
```
However, when I specify the server as the default IPv6 router on my clients, it doesn't seem to route anything (the server's own default IPv6 gateway is still the IPv6 router, of course):

```
$ traceroute6 -n ipv6.l.google.com
traceroute to ipv6.l.google.com (2a00:1450:4001:803::1006) from 2001:470:28:20f::107, 30 hops max, 24 byte packets
 1  2001:470:28:20f::4  3.032 ms  2.997 ms  3.045 ms
 2  * * *
etc.
```
where the server's IP address is 2001:470:28:20f::4. The client has no problem connecting to the server itself.

What did I miss?

---

