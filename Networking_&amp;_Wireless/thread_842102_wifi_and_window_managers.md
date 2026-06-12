---
title: "wifi and window managers"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by puppyfarts on 2008-06-27
I've had this problem with all Linuxes (Linuxi?)...

In Gnome, KDE, any desktop environment, wireless works. But in window managers, nope. I always have to start nm-applet, or something of the like.

Let's say I don't install a desktop environment, and I JUST use a window manager... how can I make sure wireless works?

---

### Post by dominiquec on 2008-06-27
If you just want to be sure that your Wifi works, you can open a terminal and run iwconfig.

However, if you actually want a decent replacement for nm-applet when working with another window manager, try wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)).  It's what I'm using right now with OpenBox.

Not on the main repositories yet, but it's already packaged for Ubuntu.  Follow instructions on the web site.

HTH.

---

### Post by puppyfarts on 2008-06-27
> **dominiquec said:**
> If you just want to be sure that your Wifi works, you can open a terminal and run iwconfig.

However, if you actually want a decent replacement for nm-applet when working with another window manager, try wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)).  It's what I'm using right now with OpenBox.

Not on the main repositories yet, but it's already packaged for Ubuntu.  Follow instructions on the web site.

HTH.

Thanks. I will read up on it.

---

