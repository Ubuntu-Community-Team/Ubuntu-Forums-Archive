---
title: "First install freezes upon booting"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by GX360 on 2009-01-07
Originally I was installing 8.04 LTS off a disk I had ordered months ago and never got around to it. Upon using that disk it would boot into a screen with a "Install" window that came up with distorted graphics and would freeze immediately.

After some advice from a friend I burned the Alternate installer, went through the initial installation process and partitioned my hard drive and finished the install. When I boot into Ubuntu the system seems to be working properly while prompting me for my user name and password, but immediately freezes as soon as the desktop loads, sometimes it will be a few seconds later after it finds my wireless network. Regardless my system freezes after no more then 8 seconds.

My hardware is:
Athlon X2 3800+
1Gb Corsair XMS
250GB WD sata hard drive
EVGA 7800GT
EVGA Nforce N41 mobo

I am at a complete dead end as far as to what to do now, any and all advice is greatly appreciated

---

### Post by byenary on 2009-01-07
might be some trouble loading X, try doing ctrl-alt-F1
than log in en type sudo use dpkg-reconfigure xserver-xorg, this reconfigures you x and might help...

---

