---
title: "Gnome-ppp"
date: 2004-12-28
forum: Networking &amp; Wireless
---

### Post by Smash on 2004-12-28
Hello, i've installed gnome-ppp to connect, but i have some dependencies not resolved, and when i start Synaptic, it "force" me to remove it.
Without this, i can't connect with pon or wvdial!
I have an Smlink Winmodem.
Please, help me!

TNX

---

### Post by az on 2004-12-28
Gnome-ppp uses wvdial.  If it works with gnome-ppp and wvdial does not work, you do not have it properly configure.

Also,   where did you get the package from?  Did you look in the warty backports?  There probably is a version there that has the proper dependancies...

I would reccommend:
sudo pppconfig
and use modem lights applet (pon and poff are the default commands and you just have to correct the device name in the lockfile...)

---

