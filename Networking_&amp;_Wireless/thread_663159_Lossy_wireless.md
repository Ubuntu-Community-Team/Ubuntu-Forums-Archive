---
title: "Lossy wireless"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by bitmonkey on 2008-01-09
Hi all,

I recently install ubuntu (Gutsy) on an old fujitsu siemens laptop. Much is working fine, but the wireless is flaky. I'm using a belkin 54g F5D7010 pcmcia card and connecting to a buffalo router - I've also tried with a linksys router and experienced the same symptoms. The symptoms are that the card will sometimes not connect at all (this is relatively rare, and not the main problem) and when this happens iwconfig shows it hunting for the channel and not connecting - this can usually be resolved by changing something in network manager, saving then changing it back again to update the config and presumably restart the network, since an ifdown eth1 ifup eth1 also resolves it.

The main issue is dropped packets when the network is connected. Loading webpages is slow because it is often necessary to wait for several seconds before the download starts, then it completes at a reasonable rate. Downloads with say apt-get vary between 20% and 50% of the speed the line should get. Pings show large gaps in the seq numbers, and latencies are from 30ms upwards, averaging around 100ms to the local router, pings from an xp box on the same network are 1-3ms, and pings from the ubuntu box with a wired connection are similarly fast.

Altering rates to say 1 or 2 mbps with iwconfig seems to improve things a little, but doesn't result in a satisfactory speed. I am using the broadcom chipset drivers in the "restricted drivers" admin item from the standard gutsy install - in that sense it worked straight out of the box, but the flakiness and dropped pings have been unresolvable despite doing the usual ipv6 disabling.

Any ideas?

---

### Post by krazyj on 2008-01-16
Hey there, Im trying to get the same problem fixed. Heres a link to my thread so you can follow it and hopefully it can be of help to you:
[http://ubuntuforums.org/showthread.php?t=668902](http://ubuntuforums.org/showthread.php?t=668902)

---

