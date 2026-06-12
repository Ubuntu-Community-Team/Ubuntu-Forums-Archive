---
title: "Wireless NIC works in LIVE CD, but ..."
date: 2005-06-09
forum: Networking &amp; Wireless
---

### Post by Verlager on 2005-06-09
Returned to Linux after a year long abscence, I tried the Linux Ubuntu 5.04 Live CD and it self-configured the Xterasys 54Mbps 802.11g wireless NIC beautifully. Convinced I was on to something good, I installed the system on a HD, but guess what? No auto-configure of the wireless NIC available, or maybe it failed. At any rate I couldn't access the internet

What diagnostics and utils should I use to get this wireless NIC card accessing the internet?

I have a wireless LAN router, a WRT54G broadband router.

---

### Post by DeafByBeheading on 2005-11-15
I have the exact same problem. To the original poster, I got the open source driver available at [Sourceforge]("http://acx100.sourceforge.net") working with Debian using [this guide]("http://www.houseofcraig.net/acx100_howto.php"), but it was a minor pain in the butt, and these instructions don't work with the most recent versions of the driver. It worked with 0.2-pre8-plus-fixes-57, but I found that less stable than the 0.2-pre8-plus-fixes-51 used in the guide. There is a version from just a few days ago, but I wasn't able to get it working. Then I lost my Debian install in a Windows reinstall (it totally trashed the partition table and I wasn't able to recover it). I used the Ubuntu 5.04 Live CD for recovery and was very pleasantly surprised to find the NIC working right off the bat. Very impressed by this (it worked under neither Debian nor FreeBSD 6.0), I proceeded to install, and, like you, was rather disappointed to find that wifi was out (not to mention that it has some minor problems with my CD drive which the Live CD had no problems with)...

So, any ideas? I'm happy to update to Breezy if the fix has been incorporated, or if someone has a good current, up-to-date guide to the open-source ACX driver, I'd be happy to use that. The thing is, if the Live CD has it working, how hard can it be?

---

