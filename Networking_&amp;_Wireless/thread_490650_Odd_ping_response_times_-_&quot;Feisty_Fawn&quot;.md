---
title: "Odd ping response times - &quot;Feisty Fawn&quot;"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by olaph on 2007-07-02
Distro: Ubuntu Server 7.04
2.6.20-16-server #2 SMP Thu Jun 7 20:26:23 UTC 2007 i686 GNU/Linux

When I ping hosts from my ubuntu linux box, I get inaccurate (seemingly rounded) response times from any host.

Any idea what would cause this?  More importantly, is it possible to change this behavior?

Example ping from ubuntu server:

# ping -c5 -n yahoo.com
PING yahoo.com (66.94.234.13) 56(84) bytes of data.
64 bytes from 66.94.234.13: icmp_seq=1 ttl=49 time=80.0 ms
64 bytes from 66.94.234.13: icmp_seq=2 ttl=49 time=90.0 ms
64 bytes from 66.94.234.13: icmp_seq=3 ttl=49 time=70.0 ms
64 bytes from 66.94.234.13: icmp_seq=4 ttl=49 time=70.0 ms
64 bytes from 66.94.234.13: icmp_seq=5 ttl=48 time=70.0 ms

Example from another host, on the same LAN:

# ping -c 5 66.94.234.13
PING 66.94.234.13 (66.94.234.13): 56 data bytes
64 bytes from 66.94.234.13: icmp_seq=0 ttl=53 time=77.4 ms
64 bytes from 66.94.234.13: icmp_seq=1 ttl=53 time=73.6 ms
64 bytes from 66.94.234.13: icmp_seq=2 ttl=53 time=76.4 ms
64 bytes from 66.94.234.13: icmp_seq=3 ttl=53 time=74.6 ms
64 bytes from 66.94.234.13: icmp_seq=4 ttl=53 time=81.9 ms

Thank you,

-Sean

---

