---
title: "Lock Screen"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by newlinuxuser2008 on 2008-12-20
How do i customize this screen

i want to remove switch user & leave message or just switch user

????

---

### Post by Nepherte on 2008-12-20
You can remove the switch user option in gconf-editor. Open up gconf-editor:
```
gconf-editor
```
and navigate to apps > gnome-screensaver. Uncheck the "user_switch_enabled" option.

---

