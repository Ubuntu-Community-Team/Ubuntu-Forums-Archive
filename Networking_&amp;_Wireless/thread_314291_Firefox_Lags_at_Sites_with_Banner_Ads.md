---
title: "Firefox Lags at Sites with Banner Ads???"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by deepwave on 2006-12-07
For a while I found that Firefox 2.0 seems to lag.  At first I thought the problem revolved around an application to application issue (opening links from Thunderbird to Firefox).  Then I thought it was some sort of rumored memory leak, but Firefox plays nicely with the CPU.  Finally I disabled the IPV6 resolution option in both Firefox and Thunderbird:

network.dns.disableIPv6: true


Nothing worked, until I noticed that when I had a tab of a site with a certain banner ad, Firefox would lag as the banner refreshed itself or changed images.  So inbetween frames, both the ad and Firefox would lag.  Any ideas why this occurs?  Anyone figured out a way around the issue?

---

### Post by deepwave on 2006-12-07
Figured it out.  It seemed that all animated GIFs acted up.  And the cause?  The still in development Linux version of Flash 9.0 Beta 2 release.  Removing the flash plugin out of ~/.mozilla/plugins solved the issue.

---

