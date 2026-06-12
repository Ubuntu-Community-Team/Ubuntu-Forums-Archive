---
title: "iwlist with funky results!?"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by fastawdtsi on 2006-11-08
Hey everyone;
I got my BCM4311 working on Ubutnu 2.6.17; it's slow, but it works. While I was trying to figure out why the connection was so dog slow, I noticed that when I do an 'iwlist eth1 bitrate' I get some extremely low values:

eth1      12 available bit-rates :
          0.012 kb/s
          0.018 kb/s
          0.024 kb/s
          0.036 kb/s
          0.048 kb/s
          0.072 kb/s
          0.096 kb/s
          0.108 kb/s
          0.002 kb/s
          0.004 kb/s
          0.011 kb/s
          0.022 kb/s
          Current Bit Rate:11 Mb/s

Any ideas? Could this be a reason why my connection is so slow? I'm using a linksys (cisco) B/G router, with pretty much factory settings (except the route name).

Any help would be greatly appreciated!

Thanks!

Ernie

---

### Post by fastawdtsi on 2006-11-08
Oh yeah, I'm running a 64bit flavor of Ubuntu (AMD Turion processor).

---

### Post by fastawdtsi on 2006-11-09
Are those bitrate results ok?

---

### Post by fastawdtsi on 2006-11-13
Anyone?

---

### Post by spd106 on 2006-11-13
Since Broadcom have been reluctant to work with the community on building drivers for these cards I wouldn't expect too much from them in terms of features. For example when using ndiswrapper the signal strength is always reported as 100%. The situation may improve as the specs are reverse engineered.

Try timing a large data transfer if you want to know the real speed.

---

