---
title: "Intel 8265/8275 drops connection every few seconds - Ubuntu 24.04 LTS"
date: 2024-08-25
forum: Networking &amp; Wireless
---

### Post by dwater on 2024-08-25
As per pinned instructions:

[https://dpaste.com/48MLK59T8](https://dpaste.com/48MLK59T8)

Pinging the default route shows the disconnection:

```

64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=3.81 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=3.31 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=12.5 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=1.70 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=3.19 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=4.91 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=4.36 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=13.2 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=4.59 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=2.67 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=4.17 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=4.15 ms
From 192.168.1.221 icmp_seq=24 Destination Host Unreachable
From 192.168.1.221 icmp_seq=25 Destination Host Unreachable
From 192.168.1.221 icmp_seq=26 Destination Host Unreachable
64 bytes from 192.168.1.1: icmp_seq=27 ttl=64 time=201 ms
From 192.168.1.221 icmp_seq=28 Destination Host Unreachable
From 192.168.1.221 icmp_seq=29 Destination Host Unreachable
From 192.168.1.221 icmp_seq=30 Destination Host Unreachable
64 bytes from 192.168.1.1: icmp_seq=31 ttl=64 time=9.95 ms
64 bytes from 192.168.1.1: icmp_seq=32 ttl=64 time=9.92 ms
64 bytes from 192.168.1.1: icmp_seq=33 ttl=64 time=7.59 ms
64 bytes from 192.168.1.1: icmp_seq=34 ttl=64 time=2.37 ms
64 bytes from 192.168.1.1: icmp_seq=35 ttl=64 time=3.58 ms

```

I had presumed it was a h/w problem since it is quite hot here this summer, but I see a lot of references to similar, so maybe it isn't.

Any ideas?

---

### Post by currentshaft on 2024-08-25
Move closer to the AP or change wireless channels.

---

