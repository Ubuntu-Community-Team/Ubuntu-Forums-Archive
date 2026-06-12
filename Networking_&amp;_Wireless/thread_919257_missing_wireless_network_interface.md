---
title: "missing wireless network interface"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by sliverdragon37 on 2008-09-13
I recently bought an asus m50vm-x1 laptop, and used the pre-existing data partition as an ubuntu install partition. i have been running ubuntu on my desktop for about a year and a half now. to get things up and running, i installed the windows wireless driver (netathwx) for my wireless card (an atheros ar928x). however, in the network control panel there are only 2 networks, point to point and wired. ndiswrapper reports no problems, driver correctly installed and hardware present, but nothing brings up a wireless interface. i have tried adding

auto wlan0
iface wlan0 inet dhcp

to my /etc/network/interfaces file but that hasn't done anything. i've tried modprobing ndiswrapper (maybe incorrectly) but that hasn't helped. i'm pretty stuck.

---

### Post by ARam1024 on 2009-02-11
I had problems with the AR928X wireless on my ASUS M50VM-B1.  I'm pretty sure I've solved my problem.  I've been keeping track of it in this [post]("http://ubuntuforums.org/showthread.php?p=6719143#post6719143").

---

