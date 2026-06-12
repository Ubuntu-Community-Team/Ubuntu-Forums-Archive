---
title: "Wlan0 disappeared"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by chimerical_brio on 2007-03-04
I'm trying to get my USB wireless adaptor (Linksys WUSB11v4) on a fresh install of Edgy. I used [this]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29") tutorial to get it working, and indeed, it worked. I restarted, wlan0 was still there and working great, and the Update Manager popped up. I don't remember exactly what updates it was going to install, but I do remember something about linux-headers. For some reason (I can't remember why), I tried to restart X, the computer froze, and when I manually turned off the computer and turned it on again, wlan0 didn't show up. However, when I do "ndiswrapper -l" it shows the driver as installed and the device as plugged in; likewise, when I do "lsusb" the device is shown and recognized as WUSB11v4. It just won't show up in iwconfig, even though there is an entry for it in /etc/network/interfaces. Wireless connection is also no longer an option in Networking from Administration. Can someone help me? Thanks a lot.

---

### Post by chimerical_brio on 2007-03-04
Also, after searching the forums, I noticed that other people had a problem where wlan0 would disappear, but reappear as eth1. That's not happening for me.

---

### Post by chimerical_brio on 2007-03-04
I'm really sorry to bump my topic, but I have no internet and that's a rather large problem. If no one has any ideas how I can solve this, do you have any suggestions as to other places I could go to figure out the problem? Again, thanks.

---

### Post by xdevnull on 2007-03-04
If you updated the headers - did you update the kernel?  If so you may need to resintall/redo ndsiwrapper.  You can unload it from the kernel and start from scratch, using the previous tutorial.  At least that's what I would try.  Don't know if that will hope.

---

