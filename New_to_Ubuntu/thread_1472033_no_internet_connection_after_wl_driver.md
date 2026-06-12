---
title: "no internet connection after wl driver"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by herbert tamayo on 2010-05-04
Hi, I was setting up my wireless card -broadcom 4312, I used the hardware manager option, so the driver wl was downloaded and installed automatically, after that I did a lsmod | grep wl and in fact, the modules running were wl and 80211_crypt; but the gnome-nm applet never showed in the mainbar, so I tried to configure myself the wireless using the "network applet", but after put the info of my access point i couldn't connect to internet but even using eth0 -wired network- i deactivated the wireless but still can't connect. i did also networkin restart, eth0 ifdown|ifup but nothing.

my question is: what things should I deactivated to get wired-connection again? what is happening?

regards

---

### Post by clhsharky on 2010-05-04
HI herbert tamayo

A network restart should have worked, try a system restart.

Sharky

---

