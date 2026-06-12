---
title: "launch and close graphical user interface"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by fdelval on 2010-02-16
Ey all

As i installed the fluxbox environment, i could start it from console by writing STARTX

But now i just want something more, a streamlined gnome, and i dont know how to launch it from command line, and how to shut it down and go back to command line from graphical.

---

### Post by nothingspecial on 2010-02-16
Try editing /etc/X11/xinit/xinitrc and replacing fluxbox with

```
/usr/bin/gnome-session
```

I`d back up your xinitrc before you do this, just incase.

---

