---
title: "just plain dumb top panel"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-12-09
From left to right i have the following:

show desktop | window list | <<<<<<<<<<<<<>>>>>>>>>>>> notification bar, notification applet.


now with all of these "locked to panel" you'd think they would stay in one place, but everytime i reboot, the right portion on the bar shifts to the left, almost to the middle of the panel. Why is this happening?

---

### Post by gimcrack on 2009-12-09
There is an easy way to lock down all the panels at once. Just install Ubuntu Tweak. You can install it from the Synaptic Package Manager (ubuntu-tweak), or if it is not listed go to [http://ubuntu-tweak.com](http://ubuntu-tweak.com). After you install it, a launcher will be in Applications>System Tools.

When you run this program, click on System. There is a checkbox for "Complete lockdown of the panel".

better solution all
hit Alt-F2 and run gconf-editor

when you run it navigate to

apps->panel->global

under lock_down click the checkbox

and restart gnome with Ctrl-Alt-Backspace

---

### Post by JamesParnell on 2009-12-09
thanks, i already have UT installed, i will do this now.

---

### Post by JamesParnell on 2009-12-09
couldnt find said tick box in UT, but after clicking "locked down" in gconf, and restarting gnome (actually logged in and out) the first thing it did was move again

---

