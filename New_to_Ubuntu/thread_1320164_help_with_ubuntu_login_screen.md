---
title: "help with ubuntu login screen"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by itsbrad212 on 2009-11-09
I tried to install the xfce desktop, but it didn't work so i uninstalled it. but now when i go to log in, instead of the karmic black screen with the loading bar, its  a brownish-orangish color. and that is the same for the login background. please help. i dont know if its a package that needs to be installed or something.

---

### Post by jbrown96 on 2009-11-09
Gnome and XFCE have some common dependencies, so it's possible that something was removed. Try running ```
sudo apt-get install gnome-desktop
```

---

### Post by cariboo on 2009-11-09
Try reinstalling gdm. What was it that didn't work when you installed the xfce desktop?

---

### Post by itsbrad212 on 2009-11-09
> **jbrown96 said:**
> Gnome and XFCE have some common dependencies, so it's possible that something was removed. Try running ```
sudo apt-get install gnome-desktop
```

thanks. it worked!

---

