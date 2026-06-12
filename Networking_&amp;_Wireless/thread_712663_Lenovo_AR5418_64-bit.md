---
title: "Lenovo AR5418 64-bit"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by mike665 on 2008-03-01
I have done a lot of searches and am having a lot of trouble. Am I correct thinking that the AR5418 wireless card will not work with the 64-bit version of Ubuntu?

Thank you.

---

### Post by kevmitch on 2008-03-03
AR5418 will work in 64-bit. Kind of. I'm doing it at any rate.

The problem is that you must use madwifi rather than the more stable and reliable ndiswrapper since only 32 bit XP drivers exist.

The problem is that only the pre-release subversion snapshot of madwifi supports this chip, so you will have to download that and compile it rather than downloading the version in the Ubuntu repositories. Here is the howto: [http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008)

That however, is not without it's fair share of problems: [http://www.thinkwiki.org/wiki/ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter#Problems.2FBugs.3F](http://www.thinkwiki.org/wiki/ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter#Problems.2FBugs.3F)

To summarise, you may or may not experience random disconnections (I find it works fine for me at home with the Dlink DIR-655, but not so much in several coffee shops). It may depend on the router, or possibly the amount of wireless traffic on it. There is also the issue that it has the annoying tendency to cause an NMI rendering the wifi useless until you put the machine to sleep and wake it up again. This seems to happen regardless of the router you're using.

If you crave stability rather than leading edge 64 bit performance, sticking with 32 bit will allow you to use ndiswrapper which I have found to work flawlessly. I keep a dual boot system primarily for this reason. Neither solution however will let you use draft n.

---

