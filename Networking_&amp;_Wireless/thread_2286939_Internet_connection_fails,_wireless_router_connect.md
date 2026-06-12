---
title: "Internet connection fails, wireless router connection normal"
date: 2015-07-15
forum: Networking &amp; Wireless
---

### Post by jimmy35 on 2015-07-15
My problem is functionally similar to

"[Solved] Wi-Fi losing internet connectivity, although connection still detected." [http://ubuntuforums.org/showthread.php?t=2286225](http://ubuntuforums.org/showthread.php?t=2286225)
"Wifi connected but no internet , lenovo y50-70" [URL="http://ubuntuforums.org/showthread.php?t=2286838"]http://ubuntuforums.org/showthread.php?t=2286838
[/URL]
Nevertheless, despite trying several suggestions found there and throughout the internet, the problem is not solved.

My system is a new build with a fresh install of Ubuntu 14.04.  My wireless adapter is the ASUS USB-N13 rev.B1 (recommended somewhere for Ubuntu).  The internet connection is fine for a minute or two, then fails (no browsing or pinging), although the WLAN connection seems to remain normal as evinced by the Network Manager.  The internet connection is consistently restored temporarily by disabling/re-enabling Wi-Fi from within the Network Manager.

The result of the wireless-info diagnostic script found on this forum yields substantially the same result when the internet connection is working and [when it is not]("http://paste.ubuntu.com/11884979/").

Any advice is appreciated (including comments concerning forum etiquette).

---

### Post by weatherman2 on 2015-07-15
I have a couple of these dongles.  They work OK but I have occasionally had problems just like you describe - sometimes the internet connection is working fine, then a few minutes later it drops to nothing...then it might come back.  This is with Ubuntu 12.04, but I built the driver for it myself using source code from Realtek.  I had thought that in 14.04 the default driver had been updated so you wouldn't need to do that anymore...

Anyway, a few suggestions:

- login to your router and see if the configuration is set to "WPA2 + WPA Personal"  If it is, change it to just "WPA2 Personal."  (Not including WPA.)  I have seen cases where having both enabled will cause connection problems.  Pretty much everything should support WPA2 nowadays.

- what is the physical location of the wireless card/computer relative to the router?  Try the common sense stuff of moving things closer or removing physical obstructions between the router and the computer/wireless card that could interfere with the WiFi radio.

---

### Post by jimmy35 on 2015-07-15
Thanks for your suggestions:

-I avoided the WPA2-only suggestion earlier because I didn't know the credentials to log-in to the router.  I finally got them and tried this, but the behavior is the same.

-The router is about 15 straight feet away, upstairs.  I don't think I have an electromagnetic propagation issue.  The Windows laptop connectivity is fine.

---

### Post by weatherman2 on 2015-07-15
OK - so you're saying you use the same wireless card/same laptop in Windows and it works fine just not in Ubuntu?

---

### Post by weatherman2 on 2015-07-15
OK, I plugged my RTL8192CU dongle into my latest 14.04 build.  Sadly, it seems the driver is STILL broken since the last time I visited this issue back in 12.04.  I had similar connectivity issues to what you describe.

Alas, there is an easy solution, if you are able temporarily to plug the system into wired internet and copy-and-paste a few commands into a terminal window. I followed this guide to a tee and in about five minutes I had a working driver:

[https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7)

At least it's a little easier now than it was a few years ago to build a new driver...

---

### Post by jimmy35 on 2015-07-16
I built and installed the new driver and you solved my problem.  I'll figure out how to mark it solved.

To celebrate I watched the Ristar ending:
[https://www.youtube.com/watch?v=lItZtx7Bo6s](https://www.youtube.com/watch?v=lItZtx7Bo6s)

---

### Post by weatherman2 on 2015-07-16
Great.  One caveat: you may need to repeat this process each time you update the kernel - not sure.  (In the past, this was required when manually building the wireless driver.)  Just FYI - in case you update and reboot and suddenly your wireless is gone.  Or maybe not - maybe it will automatically update now...

---

