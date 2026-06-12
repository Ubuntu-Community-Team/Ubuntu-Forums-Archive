---
title: "VNC connects, but all I get is the splash screen?"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by Kuma_Pageworks on 2007-02-09
When I connect to my 6.10 box with VNC, all I get is a weird waffle-weave background and the Ubuntu splash that normally shows GNOME starting up.  I can't do anything else with the session at all.

I've tried creating the xstatup file and putting it in my .vnc folder to start GNOME on connection, but the documentation for VNC doesn't have anything on syntax, or even if that's the right place to put it.

Any help?

---

### Post by zymorph on 2007-02-09
check this out ... [https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282) ... basically the current solution is to downgrade your version of vnc4server because there is a bug in the latest version for edgy 6.10.

> **Kuma_Pageworks said:**
> When I connect to my 6.10 box with VNC, all I get is a weird waffle-weave background and the Ubuntu splash that normally shows GNOME starting up.  I can't do anything else with the session at all.

I've tried creating the xstatup file and putting it in my .vnc folder to start GNOME on connection, but the documentation for VNC doesn't have anything on syntax, or even if that's the right place to put it.

Any help?

---

### Post by kebes on 2007-02-09
I had a similar problem once:
[http://www.ubuntuforums.org/showthread.php?t=232940](http://www.ubuntuforums.org/showthread.php?t=232940)

The fix was simple. All I had to do was modify my "~./vnc/xstartup" file, and change the last line from "x-window-manager &" to:
```
startkde &
```

That's to start-up KDE, obviously. If you're running Ubuntu and want to start up GNOME, then make the last line "gnome-session &".


I'm not sure if what you're running into is the same thing (you said you see an Ubuntu splash screen??), but maybe that will provide some hints...

---

