---
title: "xubuntu and rt2500 wireless"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by king_weaver on 2007-06-15
Ok so im trying to get my xubuntu 7.04 install ironed out. Heres the deal its installed on an averatec 3700 series laptop that uses the ralink rt2500 wireless chipset. Ive read several how-to's and quick fixes on getting this wireless card to work, but all of them are different and all are very confusing. Ive tried installing the newest drivers but everytime I get to the "make file" step it gives me an error saying "wireless networking is not enabled" and another saying "debugfs is not enabled" and wont let me continue...im at a complete loss here. could someone walk me through what to do step by step? I would really appreciate it.

---

### Post by dliberal on 2007-06-15
I think you have the same problem as I do. I've been searching and I discovered that feisty have several problems with that wireless card:
[https://launchpad.net/ubuntu/+source/network-manager/+bug/78037](https://launchpad.net/ubuntu/+source/network-manager/+bug/78037)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103623](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103623)

I haven't been able to fix mine, even with the workarounds, so good luck!

---

