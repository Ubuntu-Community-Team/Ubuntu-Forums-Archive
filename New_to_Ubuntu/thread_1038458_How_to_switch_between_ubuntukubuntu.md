---
title: "How to switch between ubuntu/kubuntu"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Teegoat on 2009-01-12
Hi everybody,
I've just installed KDE desktop to try it out in my Ubuntu, but I don't know how to switch into Kubuntu hassle-free and then back to ubuntu.
Also, how do I get the Ubuntu start/finish screen back?

---

### Post by whoop on 2009-01-12
There should be an options button on the login screen to select the desired window manager.

---

### Post by bodhi.zazen on 2009-01-12
> **Teegoat said:**
> Hi everybody,
I've just installed KDE desktop to try it out in my Ubuntu, but I don't know how to switch into Kubuntu hassle-free and then back to ubuntu.
Also, how do I get the Ubuntu start/finish screen back?

To return you "ubuntu" log in screen :

```
sudo dpkg-reconfigure gdm
```

From the options list select gdm.

To change between gnome and kde, use the options on the log in screen.

---

