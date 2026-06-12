---
title: "Ubuntu installation affecting router?"
date: 2019-09-26
forum: Networking &amp; Wireless
---

### Post by Dy1anW on 2019-09-26
Hi!

So, a few months back I had upgraded from Ubuntu 16.04 to 18.04 on my desktop which is connected to the router by ethernet. This is when I start noticing really strange things that happen consistently, namely: my laptop, phone, or printer will not connect to the router via WiFi. In fact the router can't even be found. I never had this problem when using 16.04. This issue occurs as soon as I boot into Ubuntu. I don't get this problem when I boot the desktop into Windows 10; everything can connect to the router no problem at all.

Another detail: if I leave my desktop in the Ubuntu partition for about a day, the wired connection fails as well!!

I don't know why, but it really seems like Ubuntu 18.04 on my desktop is screwing up my router. It's very bizarre!

Just to reiterate the point: there's no issue with any of my wireless devices, but WiFi on my router dies inexplicably only when running Ubuntu 18.04.

Any ideas what's causing that, and how to solve it?

Many thanks!

---

### Post by TheFu on 2019-09-27
Using wired ethernet would be better in 50 other ways to

Netgear wifi?  I've seen this issue many places across many different Linux distros and hardware running it.  There are certainly AP settings to make it work, but I've never found them. My solution is to get a Ubiquiti AP connect it to the netgear router and disable the netgear wifi.  That has always, 100%, solved the issue in less than 1 hour rate to the client. Initially, I would waste 5 hrs trying to get it working, but soon learned that $80 solves this issue and provides much better wifi coverage.

So, if you still want to try to make wifi work using the existing stuff, post all the details about the wifi hardware on both sides, all the driver settings too. I think there's a *wifi-info* script somewhere.  Might be called *wireless-info* script. That only gets the Ubuntu side. The router wifi settings are needed too.

---

### Post by Dy1anW on 2019-09-30
Hi, thanks for the reply.

Yes, it is indeed Netgear wifi. So I take it this is a well known problem? I could go and look for a Ubiquiti AP, but I'm concerned that while it'll solve the issue of wifi disappearing, there's still the problem of the wired connection from my desktop dying after a day. Actually last night the wired connection died some time within 8 hours.

The above may be a bit misleading, having just read it back. The problem on the wired side is that since I upgraded my desktop to 18.04, after x number of hours (it seems to be random now that I think about it) it kills my connection to the ISP, but I can still connect to the router from my desktop. That being the case, even with an auxiliary wireless AP, I may be able to connect my other devices to wifi, but they still won't be able to communicate to the net.

Well, I'll have to double check on the wired situation. Will post details of wireless settings later.

As for the router, it's quite an old one, so maybe that's a factor? Just to give some idea how old it is, I bought it around the release date of 802.11n. I think it was such an early model that 802.11n was still "experimental" or "not finalised", or something along those lines. I don't see why the router would have problems with 18.04, and no issue with 16.04 though, but this whole thing is quite bizarre.

---

### Post by TheFu on 2019-09-30
Is the firmware on the Netgear current - like less than 3 months old? There have been necessary security updates to routers multiple times every year.  If the firmware updated ended more than 3 months ago, it is time to either buy a new router or get off the 3-yr router hardware upgrade and use an after-market firmware for as long as it is supported and maintained.

Have you checked the power management network settings?  To save battery, networking is often turned off as a standard method.

---

### Post by Dy1anW on 2019-10-16
Hi again,

The firmware hasn't been updated for quite a while, so yeah, maybe it is time for an upgrade. It's still odd that wireless stops working only when running Ubuntu on my desktop. It's definitely on the router side as it turns out that nothing can connect to it, wired or wireless. Even my broadband TV decoder won't connect to the router. A couple nights ago the router did its thing within 10 mins of switching my desktop from Windows to Ubuntu.

---

