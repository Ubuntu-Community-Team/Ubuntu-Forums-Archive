---
title: "[SOLVED] Major blockage in first HOP"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by x1a4 on 2008-06-07
Hi,

I've a slowdown of internet traffic and did a traceroute to my site with the following results:
```

traceroute to hex1a4.net (67.55.45.207), 30 hops max, 40 byte packets
 1  * * *
 2  dsl (67.204.8.1)  10.039 ms  10.637 ms  11.614 ms
 3  66.49.255.209 (66.49.255.209)  13.675 ms  15.283 ms  17.473 ms
 4  66.49.255.6 (66.49.255.6)  19.220 ms  20.537 ms  22.273 ms
 5  67.55.32.230 (67.55.32.230)  24.196 ms  25.432 ms  27.344 ms

```

Obviously there's a major blockage in first HOP, and I have no idea how it happened or how to fix it.  The problem is not with the ISP, I already checked.

Any ideas?

Thank you.

---

### Post by fwre01 on 2008-06-07
i dont think a trace nessersarily proves a blockage, it means that particular hop doesnt respond to ICMP TTL expired packets. Your first hop is usually your default gateway.

your ping times might be a better indication of a slow internet connection

---

### Post by x1a4 on 2008-06-09
Thanks.  You were right it's not a blockage.  I was checking my internet connection because my site was loading very slowly and I wanted to ensure it's something wrong with the server and not on my end.

---

