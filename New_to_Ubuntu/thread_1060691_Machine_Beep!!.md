---
title: "Machine Beep!!"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by jtsc on 2009-02-05
In many cases (largely when I'm scrolling through a list, and I hit the end, or nothing comes up in a search), Ubuntu (or Gnome, or the apps) makes a high pitched beep that I find very unpleasant. I can't figure  out how to turn it off. Most of the relevant apps don't have sound settings, so I assume it's a system-wide thing.

---

### Post by iaculallad on 2009-02-05
Try disabling your PC speaker by editing your blacklist file located at /etc/modprobe.d folder:

```
gksudo gedit /etc/modprobe.d/blacklist
```

and add the text below on the last line of the file.

> blacklist pcspkr

Save and Close the file. While on the terminal, issue the command below to activate changes.

```
sudo rmmod pcspkr
```

HTH.

---

### Post by ad_267 on 2009-02-05
System - Preferences - Sound and untick "Play alert sound"

---

### Post by kbutcher5 on 2009-02-05
Mute the pcspeaker in volume settings?

---

### Post by Michael.Godawski on 2009-02-05
hi;

[http://ubunturesources.ub.ohost.de/systembeep.html](http://ubunturesources.ub.ohost.de/systembeep.html)

---

### Post by jtsc on 2009-02-05
Thanks so much, everybody! Those all worked, and it's helpful to learn so much.

---

