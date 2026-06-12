---
title: "How do I use more than 30% of available bandwidth (iPerf3 test)?"
date: 2018-12-27
forum: Networking &amp; Wireless
---

### Post by madumi on 2018-12-27
I'm networked between an ubuntu server & a windows 10 machine. Network cards on both ends are both Asus XG-C100C (10Gb/s NIC card).

Network is rock solid & cards/drivers work well.

However... When I transfer files, the network seems to saturate at about 3Gb/s. Similarly, an iPerf3 test will saturate at about 3Gb/s (3.16 if Jumbo packets are enabled).

On the other hand, if I test iPerf3 with 3 or more parallel streams, the network saturates at 9.42Gb/s.

Are there any settings I can tweak to better utilize available network bandwidth? 30% of 10Gb/s is great, but more would be better, right?

thanks!

---

### Post by TheFu on 2018-12-28
Could it be a bug in iperf? [https://github.com/esnet/iperf/issues/220](https://github.com/esnet/iperf/issues/220)
Have you tried with IPv4 only?  IPv6 only?

I've never touched 10G networking stuff, but if multiple streams do work, it seems like a programming bug.

---

