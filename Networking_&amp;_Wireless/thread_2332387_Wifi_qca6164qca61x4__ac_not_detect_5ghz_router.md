---
title: "Wifi qca6164/qca61x4  ac not detect 5ghz router"
date: 2016-07-31
forum: Networking &amp; Wireless
---

### Post by virgosun on 2016-07-31
Hi,

As in title my wifi work well with 2.4ghz but not detect 5.8ghz from the same router
pls help
[IMG]http://i.imgur.com/ge4Ay0t.png[/IMG]

---

### Post by praseodym on 2016-07-31
> ```
wlp2s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.472 GHz (Channel 13)
```
Change to one of the supported channels shown in "iwlist chan"

---

### Post by virgosun on 2016-07-31
Thank you buddy. I am at work. Will try tomorow

---

### Post by virgosun on 2016-07-31
> **praseodym said:**
> Change to one of the supported channels shown in "iwlist chan"
The router channel is out of range
Any idea
Thanks[IMG]http://i.imgur.com/g0yHekl.png[/IMG]

---

### Post by praseodym on 2016-08-01
Check if there is an update available for the router firmware

---

