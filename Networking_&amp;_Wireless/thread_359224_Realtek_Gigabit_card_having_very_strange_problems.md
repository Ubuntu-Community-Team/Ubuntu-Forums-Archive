---
title: "Realtek Gigabit card having very strange problems"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by Malviolent on 2007-02-11
I have a Realtek 8169/8110 Family Gigabit Ethernet NIC, and I'm having problems.

My network is acting very strange.  Windows works fine, but when I'm on ubuntu (6.10 edgy i386 with the latest kernel as of 2/11/07) my network rarely works properly.  It will take 30-60 seconds to connect to a website, and sometimes it doesn't even connect at all.  GAIM will rarely connect, and when it does it will not respond to traffic.

I have read that linux sets the buffer sizes for gigabit cards too low, so I tried upping my sizes to 514288 using the following command:

sudo echo > 514288 /proc/sys/net/core/rmem_max
sudo echo > 514288 /proc/sys/net/core/wmem_max

I have also tried opening the /etc/sysctl.conf and changing the values there (so they would always be changed), and sometimes it seemed to work, but only for a minute or so, then it would fail.  I'm in dire need of help (I'm close to simply reinstalling ubuntu again) thanks!

---

