---
title: "Messed around too much"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by mutesounds on 2010-05-19
I am using a laptop with an external monitor.  I was messing around in the ATI Catalyst settings and somehow screwed everything up.  The external monitor has the desktop but no toolbars or icons, the laptop has a black screen with a cursor.  How can I get it back to the way it was before?  I need to be able to access the ATI Catalyst GUI that was in Preferences but I don't know how to launch it.

Also, can I launch the Monitors gui from terminal?

---

### Post by blazemore on 2010-05-19
Try this command to reset the X-server settings:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

