---
title: "Weird USB wireless issue"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by justin_p on 2007-11-14
Well I used the livedcd for 7.10 and it detected my usb 2.0 wirelss adapted.  I could see the networks but not connect.  I figured after install I could work it since it could see the networks.  So far that hasn't worked out.  I followed some of the suggestions on this page which seems to describe the bug [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/85468](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/85468).  I messed around with my /etc/network/interfaces file so that there was an entry for 10, eth0, wlan0, wmaster0.  After restart, with the USB adapter in the whole time, the network comes back up and it says it connects to my wireless network.  But everything I try to load a page or ping it doesn't work.  I looked at my /etc/network/interfaces file and now there are entries for eth0 and wlan0 with a :avahi added to it.  Not sure if that plays a part.  I have tried to bring eth0 up and down without luck.  The connection registers strong, i get 4 bars.  But I can't get on the web.  Let me know what files you need to see and I'll move them over.  Thanks in advance.  

Justin

---

### Post by justin_p on 2007-11-15
Anyone...nothing....Buehler?

---

### Post by wieman01 on 2007-11-15
It would help if you told us what brand of wireless adapter you have got and what chipset is uses...

---

### Post by justin_p on 2007-11-15
it's a rt2500usb.

---

### Post by justin_p on 2007-11-15
Ok.  I have some more info for everyone....the devices wlan0, wmaster0 and wlan0:avahi all share the same MAC address.  So I have 3 interfaces for one device.  Interesting.  Maybe another driver is needed.  I need to this out.  But the rt2500usb is loaded on boot.

---

### Post by wieman01 on 2007-11-16
If you have a RT2500 USB you can try my tutorial (see signature). Post there if you need support.

---

