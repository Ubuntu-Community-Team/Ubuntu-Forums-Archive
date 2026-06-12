---
title: "The GNOME screensaver daemon appears to be running."
date: 2011-01-23
forum: New to Ubuntu
---

### Post by fleamour on 2011-01-23
Screensaver settings will not stick after reboot.  

When going to System>Preferences>Screensaver I get these two boxes:  

> The GNOME screensaver daemon appears to be running.  It must be stopped for XScreenSaver to work properly.  Stop the GNOME screen saver daemon now?
> The XScreenSaver daemon doesn't seem to be running on display ":0.0".  Launch it now?

GLMatrix screensaver will then work till next reboot.

---

### Post by taseedorf on 2011-01-23
for some reason, the daemon isn't starting at boot.  Either reinstall gnome screen saver package via synaptic or make a link to it in startup manager

---

### Post by fleamour on 2011-01-23
Well the Gnome daemon ***is*** running at start up.  I wonder why it needs to be stopped to run XScreenSaver daemon, which is not running on startup.  Something seems broken?

---

### Post by fleamour on 2011-01-23
OK you were along the right lines, it appears both are conflicting.  I need to uninstall one or the other.  Maybe XScreenSaver got installed with XFCE back along?

Question.  Where is the configuration for Gnome screen saver?  I uninstall X leaving me with no screensaver option under Preferences.

---

### Post by fleamour on 2011-01-23
[http://library.gnome.org/admin/system-admin-guide/stable/screensavers-2.html.en](http://library.gnome.org/admin/system-admin-guide/stable/screensavers-2.html.en)

```
/usr/bin/gnome-screensaver-preferences
```

---

