---
title: "How to disable Viino"
date: 2015-01-11
forum: Networking &amp; Wireless
---

### Post by MikeMecanic on 2015-01-11
**Can you remind me how to disable Vino in the terminal please?**

---

### Post by Irihapeti on 2015-01-11
The command is
```
sudo apt-get remove vino
```

---

### Post by steeldriver on 2015-01-11
if you simply want to disable (rather than remove) it,

```

gsettings set org.gnome.Vino enabled 'false'

```

---

### Post by MikeMecanic on 2015-01-11
Thanks problem resolve

---

### Post by wildmanne39 on 2015-01-11
This > xserver-xorg-corehas to do with your graphics card, so when you reboot you probably will not be able to see anything.

---

### Post by MikeMecanic on 2015-01-11
Black screen indeed.  Lots of problem to get out of that.  The comand:  sudo apt-get remove xserver-xorg-core shoudn"t be used.  I erase it on top.
Recover mode: $ sudo apt-get update + autoremove + autoclean disk. Ouffff :)

---

