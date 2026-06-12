---
title: "ubuntu and dlink di-604 - help with setup"
date: 2005-10-01
forum: Networking &amp; Wireless
---

### Post by a212359 on 2005-10-01
Hello. I have tried to avoid posting this, but I have tried all I know and am stuck...hopefully someone can help!

In all the cases below I am using dhcp.

If I plug the network cable directly into my ubuntu machine, it works fine.
If I go through the router, I get speeds about 5% of what I get without the router.
There is an xp machine also plugged into to the router - it works fine. If I boot the xp partiton on the ubuntu machine, and go though the router, it works fine as does the other xp machine (at the same time).

I have checked the network cable, disabled ipv6.
/etc/resolv.conf is _identical_  when it is working fast with the network cable plugged in (no router), and when it is going slow (with router).

here is the the difference in ifconfig when it is working fast (no router) and slow(with router)
```

$diff ifconfig.fast.txt ifconfig.slow.txt
2c2
<           inet addr:192.168.52.239  Bcast:192.168.55.255  Mask:255.255.252.0
---
>           inet addr:192.168.0.142  Bcast:192.168.0.255  Mask:255.255.255.0
4,5c4,5
<           RX packets:118 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:72 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
7c7
<           RX bytes:14336 (14.0 KiB)  TX bytes:3036 (2.9 KiB)
---
>           RX bytes:5792 (5.6 KiB)  TX bytes:4301 (4.2 KiB)
13,14c13,14
<           RX packets:7070 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:7070 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:8222 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:8222 errors:0 dropped:0 overruns:0 carrier:0
16c16
<           RX bytes:644896 (629.7 KiB)  TX bytes:644896 (629.7 KiB)
---
>           RX bytes:750149 (732.5 KiB)  TX bytes:750149 (732.5 KiB)
19c19
<           inet addr:212.201.72.153  P-t-P:192.168.1.168  Mask:255.255.255.255
---
>           inet addr:212.201.74.239  P-t-P:192.168.1.168  Mask:255.255.255.255
21,22c21,22
<           RX packets:10 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:9 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
24c24
<           RX bytes:127 (127.0 b)  TX bytes:115 (115.0 b)
---
>           RX bytes:111 (111.0 bt)  TX bytes:99 (99.0 b)

```
the reason for the second ip at the bottom is that I have to go though a vpn as well, but I don't think thats an issue since it works fine without the router....I really think this a ubuntu-router issue but I have no idea how to solve it...maybe other people have this router and can suggest something?

Thanks for the help.

---

