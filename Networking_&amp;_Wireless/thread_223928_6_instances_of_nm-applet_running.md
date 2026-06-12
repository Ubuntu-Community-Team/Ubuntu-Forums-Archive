---
title: "6 instances of nm-applet running"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by rlgoddard on 2006-07-27
Hi,

I am using Xubuntu 6.06 LTS, and I noticed that when firing up the xfce task manager, *six* instances of nm-applet are running.  Is that normal?  Can I turn them off without risking the lost of my network connection?  Thanks for any assistance!

Take care,
Russ

---

### Post by rlgoddard on 2006-08-18
Ok, I bit the bullet and killed all instances of nm-applet.  I still have my network connection! :-k I also turned on the system tray and noticed the six network icons, each with a red "X".  Every time I re-boot, those six icons show up.  How do I have xfce NOT load six instances of nm-applet?

Take care,
Russ

---

### Post by stani on 2006-08-18
I would suggest:

remove them manually (right-click on each of them)

sudo apt-get remove network-manager-gnome

logout while saving your session

---

### Post by stani on 2006-08-19
I have posted a howto nm-applet on xubuntu here:
[http://www.ubuntuforums.org/showthread.php?t=239178&highlight=xubuntu+nm-applet](http://www.ubuntuforums.org/showthread.php?t=239178&highlight=xubuntu+nm-applet)

Please give further reactions there.

---

