---
title: "Lower the Sensitivity of Multimedia Keys"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by NK-Magi on 2009-03-14
Is there any way to lower the amount it lowers/raises volume on a laptop media key?  I've got an HP dv4 with the touch keys with the volume bar, just wondering if you can lower the percent it goes in one press.

---

### Post by sdennie on 2009-03-15
Yes, you can.  Hit Alt-F2 and type gconf-editor.  Navigate to /apps/gnome-settings-daemon and adjust the value of volume_step.  It represents the percentage the volume changes when you hit the volume buttons.

---

### Post by NK-Magi on 2009-03-15
Wow thanks!

---

