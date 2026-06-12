---
title: "ath_hal instead of ath9k for AR5418?"
date: 2014-04-26
forum: Networking &amp; Wireless
---

### Post by sethgoldin on 2014-04-26
I'm on a MacBookPro1,1 with a clean installation of 32-bit 14.04 LTS. During the installation, I had an ethernet cable connection, so all the software is completely up-to-date.

When I unplug the ethernet cable, and run **nm-tool**, it appears that I'm connected, running **ath9k**, but I can't actually load any pages in Chrome or Firefox, though I can successfully ping websites.

Running **lshw**, I see that I have a Qualcomm Atheros AR5418 Wireless Network Adapter. I found [ath_hal]("http://manpages.ubuntu.com/manpages/trusty/en/man4/ath_hal.4freebsd.html"), which looked promising, since my card seems to supported, but I'm a Linux newbie, and don't know how to load kernel modules. Am I on the right track here? Might setting up **ath_hal** and blacklisting **ath9k** get my wireless card working? How would I do this?

I'm attempting to connect to an Arris Touchstone TG862.

---

### Post by varunendra on 2014-04-28
Welcome to the forums sethgoldin !

The ath_hal is just a supporting part of the main wireless drivers, it can't be used alone. To diagnose the problem, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by sethgoldin on 2014-04-28
After doing some more research, I suspect the issue may just be my router, Comcast's [COLOR=#000000]Arris Touchstone TG862, which doesn't seem to support Linux well. All my other Mac OS X and iOS devices work fine, so I just purchased [a different router]("http://www.amazon.com/dp/B00A3YN0Z0/"), which looks like it will work better for Linux. If not, I'll post the script report here. Thanks![/COLOR]

---

### Post by sethgoldin on 2014-04-28
Just thought I'd follow up. The WiFi on the Arris Touchstone TG862 didn't work well, but the [Medialink]("http://www.amazon.com/dp/B00A3YN0Z0/") works wonderfully. Turns out that routers that are actually designed for Linux work best...

---

