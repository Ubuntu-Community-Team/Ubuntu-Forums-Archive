---
title: "Fast growing and falling ping on ethernet and wlan"
date: 2015-08-07
forum: Networking &amp; Wireless
---

### Post by chromo2 on 2015-08-07
Hello,
I experience fast growing and falling pings to my ubuntu computer over Ethernet and WLan.
Here is, how my ping looks:
```
[COLOR=#BFBFBF][FONT=Menlo]
[/FONT][/COLOR]
[FONT=Menlo]64 bytes from 192.168.0.128: icmp_seq=1 ttl=64 time=1.890 ms[/FONT]
[FONT=Menlo]64 bytes from 192.168.0.128: icmp_seq=2 ttl=64 time=39.607 ms[/FONT]
[FONT=Menlo]64 bytes from 192.168.0.128: icmp_seq=3 ttl=64 time=63.153 ms[/FONT]
[FONT=Menlo]64 bytes from 192.168.0.128: icmp_seq=4 ttl=64 time=87.307 ms[/FONT]
[FONT=Menlo]64 bytes from 192.168.0.128: icmp_seq=5 ttl=64 time=106.353 ms[/FONT]
[FONT=Menlo]64 bytes from 192.168.0.128: icmp_seq=6 ttl=64 time=27.428 ms[/FONT]
[FONT=Menlo]64 bytes from 192.168.0.128: icmp_seq=7 ttl=64 time=51.514 ms[/FONT]
[FONT=Menlo]64 bytes from 192.168.0.128: icmp_seq=8 ttl=64 time=166.855 ms[/FONT]
[FONT=Menlo]64 bytes from 192.168.0.128: icmp_seq=9 ttl=64 time=684.495 ms[/FONT]
[FONT=Menlo]64 bytes from 192.168.0.128: icmp_seq=10 ttl=64 time=1193.864 ms[/FONT]
```

I think, It looks like a buffer is filling and when it is emptied, the ping is low again.
Can someone help me? thanks.

---

### Post by TheFu on 2015-08-09
Which is it - wireless LAN or ethernet?  The solutions are completely different.

---

