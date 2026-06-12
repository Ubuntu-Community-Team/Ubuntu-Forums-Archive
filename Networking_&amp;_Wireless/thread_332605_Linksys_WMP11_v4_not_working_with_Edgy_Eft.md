---
title: "Linksys WMP11 v4 not working with Edgy Eft"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by thijsie on 2007-01-06
Hi,

I'm having trouble getting my Linksys WMP11 v4 to get to work with Ubuntu 6.10 Edgy Eft.

This is what I have done sofar:

installed ndiswrapper-1.8 with apt-get
After installing the three divers, *ndiswrapper -l *gave me this:

[I]Installed ndis drivers:
lsbcmnds        driver present
lsipnds driver present, hardware present
wmp11nds        driver present[/I]

Then I did *modprobe ndiswrapper*.

According to what I've read, my card should show up as wlan0 in ifconfig, iwconfig or by typing *dmesg|grep ndiswrapper*, but this all gave nothing.....
I tried my best on the search, but it leaves me clueless.

Does anyone has a clue on how to get this to work?
I'd really appreciate it!

---

