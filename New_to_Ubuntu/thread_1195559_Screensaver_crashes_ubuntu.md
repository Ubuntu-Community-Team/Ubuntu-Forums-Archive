---
title: "Screensaver crashes ubuntu"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by iameatingjam on 2009-06-23
and I have to restart. I really don't want a screensaver, I was just looking at them when the preview for one of them crashed the system. For this reason I can't really change it, how can set my screensaver to none without having to open the utility for it?

---

### Post by utnubuuser on 2009-06-24
hi> [http://ubuntuforums.org/showthread.php?t=651868]("http://ubuntuforums.org/showthread.php?t=651868")

Also, if you launch the preference control panel from the command-line, you'll get error messages to pass along to launchpad (if there are any). In terminal:> gnome-screensaver-preferences

You could also try to launch the preferences from the terminal using the gksu command (gksu gnome-screensaver-preferences) to see if running the app as root makes any difference,  - that way you might be able to un-check the "Activate screensaver when computer is idle" check-box at the bottom left of the preferences window.

---

