---
title: "2wire USB adapter not working"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by Sk8Save on 2008-10-14
I just installed v.8.04 of Ubuntu and cannot link to the internet.  As far as I can tell, my 2wire wireless adapter isn't working.  I went to 2wire's site, and they have drivers only for Windows XP or Vista.  Can anyone help me figure out how to get this working?  Thanks much in advance!

jwk

---

### Post by Sk8Save on 2008-10-16
More info on this.  I have the drivers (both .inf and .sys files) and have tried using ndiswrapper (per directions on this site) to install.  When I follow the command structure, it says that the file isn't in the /etc/ndiswrapper folder (the .inf file that is).  When I try to put it in there somewhere, it won't let me (somehow, I'm not the root user).  I need to get this up because most of what I do is via the internet, and if I can access the internet with this machine, I'm stuck with Windows.

A little more info:  in the network manager, the ESSID is listed, and I have it set up for automatic configuration.  When I do the lsusb command, it does list the wi-fi adapter as "ZyDAS WLA-54L WiFi" so the machine knows it's there.

Can anyone help me get this working?

---

### Post by NoBugs! on 2009-01-06
The driver at the 2wire site doesn't seem to work, but these instructions should work:
[http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html](http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html)

---

