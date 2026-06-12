---
title: "starting KDE &amp; xfce desktop from terminal"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by flyingsliverfin on 2009-05-01
I have installed the Xfce desktop. now I want to learn about it. I know that I can switch to it by going (login screen) session-> xfce,

however, im trying to learn as much as possible about the terminal. is there a way to start it from a tty or from recovery mode? (like for gdm theres /etc/init.d/gdm restart only for Xfce)
 

the same thing for KDE too if you don't mind :)


ty in advance

---

### Post by jbrown96 on 2009-05-02
You're absolutely right about starting gdm. KDE can, unsurpisingly, be started with /etc/init.d/kdm. However, I'm not sure about XFCE. xdm is usually a general term for X-windows, so I don't think that will help. If your last session was XFCE, you may have luck with ```
startx
```

---

### Post by flyingsliverfin on 2009-05-02
ssadly for me I so far have used mostly gnome...
my default is gdm, and when I say (from recovery) /etc/init.d/kdm start   , it says something like: cannot start kdm is not default.

any way to change this temproarily?

---

### Post by jbrown96 on 2009-05-02
You will need to edit your /etc/init.d/kdm file. I found this section at line 30. ```
# To start kdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager
``` Just change the value to false, save and exit. You should be able use ```
sudo /etc/init.d/kdm start
```

---

