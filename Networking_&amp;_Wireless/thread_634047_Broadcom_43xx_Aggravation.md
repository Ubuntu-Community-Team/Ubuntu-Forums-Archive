---
title: "Broadcom 43xx Aggravation"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by gnelson on 2007-12-07
I'm trying real hard to get Ubuntu to work.  My last real source of aggravation is my wireless.  I don't want to go back to Vista!  But I use my laptop as a web developer and every hour (and there has been many) tinkering with Ubuntu is one less that I am working.

I have a HP dv6324us laptop that I bought this summer (in 20/20 hindsight I would have done more research on linux compatibility but it was the experience of using Vista on the laptop that drove me to Ubuntu).

I am really confused about the Broadcom 43xx wireless adapter.  I am using Gutsy and it's Restricted Driver Manager.  Here are my symptoms:

Most times at boot up, the wireless works fine.  I get good speed and no real problems.  However, after a random period of time - 5 minutes to 5 hours - the connection fails.  The nm-applet still shows a connection, but there isn't one.  If I try to reconnect through nm-applet, it will never reconnect.  If I select "Connect to Other Wireless Network", nm-applet crashes every time.  The only solution (that I know of) is a hard reboot.

Other times, after a boot, it will not connect at all and I have to reboot one or more times to get it to connect.

I removed security temporarily to see if that solved the problem, but it didn't.  

There are several tutorials that make use of NDISWRAPPER and/nor wpa-supplicant.  However, many of these are pre-Gutsy.  Is NDISWRAPPER an alternative or addition to the Restricted Driver Manager?  Does it work better?  The same for wpa-supplicant?

Please help!

---

### Post by gnelson on 2007-12-07
Forgot to mention in my original post ...  I would be willing to buy a reliable USB wireless adapter for my laptop.  It's worth $50 to me to solve this.  The problem is that I can't seem to find a consensus on what ones work well.

If anyone can recommend a trouble free, reliable, wireless USB adapter I'd sure appreciate it!

---

### Post by Ayuthia on 2007-12-07
> **gnelson said:**
> There are several tutorials that make use of NDISWRAPPER and/nor wpa-supplicant.  However, many of these are pre-Gutsy.  Is NDISWRAPPER an alternative or addition to the Restricted Driver Manager?  Does it work better?  The same for wpa-supplicant?
NDISwrapper is an alternative to using the Restricted Driver Manger.  When you install NDISwrapper, you will have to blacklist the bcm43xx driver so that it will not interfere with NDISwrapper.  You will hear different answers about if it works better or not.  For me, NDISwrapper is working better than bcm43xx but I have an 4311 chipset and it seems to have some transsmission problems with this kernel.  I am using the b43 (the new version of bcm43xx) with 2.6.24-rc4 kernel on Gentoo and it works well.

If you are having problems with the Restricted Driver, you can always try NDISwrapper and see if it works for you.

---

