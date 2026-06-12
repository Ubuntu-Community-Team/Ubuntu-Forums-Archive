---
title: "WG111v2 Out of the Box with Edgy?"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by rmmcgr on 2006-11-08
Hi,

I was wondering if the WG111v2 wireless USB adapter should work out of the box with **Edgy**.  I have a fresh install, and when I plug in the adapter to the USB port, I can see it in the Networking GUI tool.  Doing "ifconfig" shows it as wlan0.

Yet when I try and do a scan (iwlist), can not see anything.  Right on top of an Apple Aiport Express (which should show up as an AP).

So do I need to install something else and/or configure something else?

Or is it something to do with the fact that that the only thing I can scan for is the Aiport Express?  (Which is configured to share out my Internet connection).

Thanks for any help,
Richard

---

### Post by FrodoB on 2006-11-08
Well, I have a WG111 v2 that I have been using on a Slackware box and I plugged it into Edgy and setup the network WEP keys and ESSID and it did start working after just a few seconds.

So it appears to work out of the box. And it appears to be using the r8187 module and not ndiswrapper.

I don't know how stable this will be, but I am sending this message using it at the moment. I had to install the module for this thing using the driver from the RealTek web site on my Slackware machine and it was a bear, so I don't have a lot of confidence in it yet.

iwlist wlan0 scanning

Does work on this one.

---

