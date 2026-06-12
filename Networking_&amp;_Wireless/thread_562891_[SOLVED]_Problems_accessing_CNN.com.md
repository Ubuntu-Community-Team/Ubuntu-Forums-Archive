---
title: "[SOLVED] Problems accessing CNN.com"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by dbott67 on 2007-09-29
Hi all, 

Can anyone confirm if they are having problems accessing [www.cnn.com?](www.cnn.com?)

For the last few days, both at home and work access to the site is extremely slow (almost non-existent, really). The page does load occasionally, but the style-sheet does not, so I just get an unformatted, left justified page with no images that looks like it came right out of 1992. 

My home ISP (7 Mbps DSL) is different from my work ISP (10 Mbps fibre-optic), yet I'm experiencing the same problem on both.

The problem occurs on multiple machines and on multiple platforms (Ubuntu, Windows XP, Windows 2003 server, inside firewalls, outside firewalls).

Access to all other sites is normal.  I can't find any mention on Google of any recent network troubles for CNN, AOL or atdn.

Some further info:

Both ISPs (work & home) use the same upstream provider (Cogentco.com).  The trace route makes it past cogent's network onto atdn.net (AOL Transport Data Network) but then abruptly starts timing out:

Traceroute from home:
```
dbott@feisty:~$ traceroute www.cnn.com
traceroute: Warning: www.cnn.com has multiple addresses; using 64.236.24.12
traceroute to www.cnn.com (64.236.24.12), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0.881 ms  0.633 ms  1.202 ms
 2  172.16.87.1 (172.16.87.1)  17.557 ms  13.749 ms  14.923 ms
 3  sprint.myisp.com (xx.yy.32.1)  13.525 ms  15.011 ms  15.971 ms
 4  f0-10.na01.b011027-0.yyz01.atlas.cogentco.com (38.112.21.193)  14.749 ms  14.925 ms  14.778 ms
 5  g9-0-3503.core01.yyz02.atlas.cogentco.com (38.20.32.105)  14.741 ms  15.480 ms *
 6  v3492.mpd01.yyz01.atlas.cogentco.com (154.54.5.81)  154.813 ms  136.456 ms
 7  t7-4.mpd01.ord01.atlas.cogentco.com (154.54.7.73)  29.494 ms  30.825 ms  30.
 8  vl3490.mpd01.ord03.atlas.cogentco.com (154.54.6.206)  38.997 ms  29.038 ms
 9  verio.ord03.atlas.cogentco.com (154.54.12.82)  32.255 ms  30.012 ms  28.993
10  p16-0.aol.chcgil09.us.bb.gin.ntt.net (129.250.9.150)  29.317 ms  29.742 ms
11  bb2-chi-P0-0.atdn.net (66.185.141.86)  29.610 ms  29.677 ms  30.914 ms
12  * bb2-vie-P14-0.atdn.net (66.185.152.215)  46.863 ms  45.896 ms
13  * bb2-atm-P3-0.atdn.net (66.185.152.33)  58.141 ms  56.667 ms
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
dbott@feisty:~$

```

Traceroute from work:
```
Microsoft Windows [Version 5.2.3790]
(C) Copyright 1985-2003 Microsoft Corp.

C:\Documents and Settings\Administrator>tracert www.cnn.com

Tracing route to www.cnn.com [64.236.16.52]
over a maximum of 30 hops:

  1    <1 ms     1 ms    <1 ms  24.244.244.113
  2     1 ms     1 ms     1 ms  24.244.192.42
  3     3 ms     3 ms     3 ms  24.244.192.17
  4     3 ms     3 ms     2 ms  205.150.210.1
  5    10 ms     4 ms     *     g0-7.na21.b011027-0.yyz02.atlas.cogentco.com [38.101.48.69]
  6    17 ms    18 ms    17 ms  v3493.mpd01.yyz01.atlas.cogentco.com [154.54.5.85]
  7    96 ms    19 ms   113 ms  t7-4.mpd01.ord01.atlas.cogentco.com [154.54.7.73]
  8    17 ms    17 ms    17 ms  v3498.mpd01.ord03.atlas.cogentco.com [154.54.5.2]
  9    17 ms    17 ms    17 ms  verio.ord03.atlas.cogentco.com [154.54.12.82]
 10    37 ms    37 ms    37 ms  p16-0.aol.chcgil09.us.bb.gin.ntt.net [129.250.9.150]
 11    40 ms    41 ms    40 ms  bb2-chi-P0-0.atdn.net [66.185.141.86]
 12    38 ms    35 ms    35 ms  bb2-vie-P14-0.atdn.net [66.185.152.215]
 13    42 ms    42 ms    42 ms  bb2-atm-P3-0.atdn.net [66.185.152.33]
 14     *        *        *     Request timed out.
 15     *        *        *     Request timed out.
 16     *        *        *     Request timed out.
 17     *        *        *     Request timed out.
 18     *        *        *     Request timed out.
 19     *        *        *     Request timed out.
 20     *        *        *     Request timed out.
 21     *        *        *     Request timed out.
 22     *        *        *     Request timed out.
 23     *        *        *     Request timed out.
 24     *        *        *     Request timed out.
 25     *        *        *     Request timed out.
 26     *        *        *     Request timed out.
 27     *        *        *     Request timed out.
 28     *        *        *     Request timed out.
 29     *        *        *     Request timed out.
 30     *        *        *     Request timed out.

Trace complete.
```

Thanks,

-Dave

---

### Post by dbott67 on 2007-09-29
The problem appears to be resolved.

Normally, I use Firefox for browsing but I decided to try IE as a test and I was able to access CNN.com.  I tried using FF again, but no luck.  Then, I decided to clear the cache and then FF worked.

I'm not sure if it was coincidental or not, but everything works now.

-Dave

---

