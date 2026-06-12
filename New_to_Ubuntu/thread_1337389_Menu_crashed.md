---
title: "Menu crashed"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by iRounak on 2009-11-25
I just installed gnome-global menu and then within half a minute my menu (top menu) disappeared. I logged out, restarted etc. I even removed gnome-global menu using apt-get remove. The menu is not coming back. Firefox does not start. I get an error: "Segmentation Fault" when I type "firefox" in Terminal.
Please help.

---

### Post by iRounak on 2009-11-25
I removed these:
 gnome-globalmenu-common libglobalmenu-gnome libgnomenu0-2
  gnome-applet-globalmenu

and got Firefox working again.
Now, I am creating a new menu at the top manually.

---

