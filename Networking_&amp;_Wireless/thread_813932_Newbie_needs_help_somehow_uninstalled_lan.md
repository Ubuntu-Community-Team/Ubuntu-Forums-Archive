---
title: "Newbie needs help: somehow uninstalled lan?"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by FOBoi1122 on 2008-05-31
I think I messed up pretty bad this time. So my wireless wasn't working and I was trying to reinstall some stuff through synaptic package manager. At this time, my wired connection to the internet still worked. Next, i marked wireless-tools for removal, and wpasupplicant for reinstallation. Then I changed my mind and marked wireless-tools for reinstallation all before I hit apply. After I hit apply, and the system did all the installing/uninstalling, I resetting my computer. When i started it up, I noticed that my system could not load a notification. It toled me that hte panel encountered a problem while loading "OAFIID: GNOME_FastUserSwitchApplet" and asks me if i want to delete the applet from the configuration. Also, my wired connection notification icon disappeared and now i have absolutely no internet connection whatsoever. If anyone could help, it'd be great.... it's been bugging me for hours.

---

### Post by Sam Lars on 2008-05-31
The fast-user-switch-applet is a package that you may have removed.  The network icon is nm-applet.  Check to see if those packages are installed.

---

### Post by FOBoi1122 on 2008-05-31
since i don't have the internet on my laptop, I'm not sure how to load the fast switcher applet. Can you show me how to load it from another computer and transfer it to my laptop?

---

### Post by Sam Lars on 2008-05-31
[http://us.archive.ubuntu.com/ubuntu/pool/main/f/fast-user-switch-applet/fast-user-switch-applet_2.22.0-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/fast-user-switch-applet/fast-user-switch-applet_2.22.0-0ubuntu2_i386.deb)
That's the Hardy i386 package.  You should be able to copy it to the computer and install it.

---

