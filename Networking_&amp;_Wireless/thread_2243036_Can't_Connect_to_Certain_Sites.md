---
title: "Can't Connect to Certain Sites"
date: 2014-09-05
forum: Networking &amp; Wireless
---

### Post by uRock on 2014-09-05
I can't connect to [www.ebay.com](www.ebay.com) on this PC. I've tried Firefox, Chrome, ping, and traceroute. I can connect via other machines on my LAN, just not my PC.

The DNS lookup gets an address, but that's it. 
```
ronnie@5FDP:~$ traceroute www.ebay.com
traceroute to www.ebay.com (66.211.181.181), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  2.902 ms  3.226 ms  3.590 ms
 2  10.82.32.1 (10.82.32.1)  16.080 ms  16.312 ms  16.300 ms
 3  24-234-8-33.ptp.lvcm.net (24.234.8.33)  17.034 ms  17.272 ms  17.256 ms
 4  24-234-6-120.ptp.lvcm.net (24.234.6.120)  18.491 ms  21.328 ms  25.879 ms
 5  chndbbrc01-pos0202.rd.ph.cox.net (68.1.0.242)  97.067 ms  97.274 ms  108.807 ms
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```
```
ronnie@5FDP:~$ ping www.ebay.com
PING www.g.ebay.com (66.211.181.181) 56(84) bytes of data.
^C
--- www.g.ebay.com ping statistics ---
17 packets transmitted, 0 received, 100% packet loss, time 16127ms
```Does anyone have any thoughts on how to troubleshoot this further or fix it?

Cheers & Beers,
uRock

---

### Post by uRock on 2014-09-05
Fixed it, but I did so many things at once that I am not sure which fixed this weird problem.

Deleted network manager profiles, my system has ti wired NIC, so I switched from eth1 to eth0, changed ports on the switch, and power cycled the router, modem, and PC. I tried power cycling before and it didn't work.

---

