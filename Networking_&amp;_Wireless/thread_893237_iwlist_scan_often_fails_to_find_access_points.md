---
title: "iwlist scan often fails to find access points"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by Astro96 on 2008-08-18
Hello,
When I upgraded to Hardy I noticed that my wireless network (ipw2200) on my Dell Latitude D620 started being flaky.  Once it connected, everything would work fine but it would take a long time to find the network.  The time it took was not consistent.

I discovered that running sudo iwlist scan (as root to force an actual scan) would often return no results.  What I think is happening is that the scanning is failing to find networks (none are displayed in Network Manager either) so nothing connects until a scan finally finds the network.

I've confirmed that the network really does exist (tried on over 5 different networks) and that iwlist scan is consistently returning incorrect results.  Has anyone else seen this behavior?  Any ideas?

Andy

---

