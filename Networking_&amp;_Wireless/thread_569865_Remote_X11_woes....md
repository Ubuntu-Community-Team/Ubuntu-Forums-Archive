---
title: "Remote X11 woes..."
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by -Zeus- on 2007-10-07
Hi,

I am trying to get remote X11 working from my BSD server to my networked (wireless) Ubuntu Gutsy-build-13 laptop.  I am connecting with PuTTY 0.60 via SSH.

Here is the error:
```
Xlib: connection to "wireless4.home:0.0" refused by server
Xlib: No protocol specified
```

I already ran the command "xhost +", and I changed "DisallowTCP=true" to "DisallowTCP=false" in /etc/gdm/gdm.conf

In my Xorg.0.log the last 8 lines repeat this error:
```
AUDIT: Sun Oct  7 15:35:30 2007: 9330 X: client 3 rejected from IP 172.20.1.128
```

I can provide any other info you need.

Any help is appreciated!

EDIT: If I do ps -ef -ww|grep X, I get this line:
```
matthew   5616  5562  0 16:24 ?        00:00:00 /bin/sh /usr/share/xserver-xgl/Xgl-lockfile-wrapper :1 -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama
```

How do I remove the arg -nolisten tcp from that process?

---

