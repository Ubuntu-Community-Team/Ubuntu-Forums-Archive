---
title: "How to customise login screen?"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by Andy06 on 2010-03-16
Is there (or will there be) a way to change the login screen background and user picture?

I remember when 9.10 came out, it changed everything and there was no easy way then to change it with a GUI. Has this been changed? Does 10.04 include some type of utility to enable this?

Thanks

---

### Post by mcoleman44 on 2010-03-17
You can change the background by doing the following:
When your at the login screen press ctrl+alt+f1
login and type this
```
export DISPLAY=:0.0
sudo -u gdm gnome-control-center
```

Now switch back to the GUI ctrl+alt+f7
now you can change whatever.

---

### Post by Gone fishing on 2010-03-17
You can change the background image (remove the Mr Bean screen) by changing the images in

/usr/share/images/xsplash

---

