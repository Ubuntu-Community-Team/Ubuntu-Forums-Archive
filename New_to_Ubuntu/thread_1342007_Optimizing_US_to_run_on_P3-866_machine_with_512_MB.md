---
title: "Optimizing US to run on P3-866 machine with 512 MB RAM"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Zenith88 on 2009-11-30
This machine will be used to view PDF score files and input/play MIDI from a Yamaha DGX-520 keyboard, these will be two main uses.

On the list of to-do things are:
- turning off journaling on / ext4 partition
- disabling firewall
- disabling selinux
- stopping unnecessary daemons

Anything else I should consider?

I would compile a PIII optimized kernel as I usually do in any Linux, do I need to install any packages for that? The kernel sources probably come in a separate package.

---

### Post by ukripper on 2009-11-30
use lighter DE - either xfce or LXDE both are in repos.
for xfce
```
sudo aptitude install xubuntu-desktop
```
for lxde
```
sudo aptitude install lxde
```

i recommend lxde based on openbox - more info here [http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html](http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html)

---

### Post by Zenith88 on 2009-11-30
Can I still run gnome applications such as Audacity under lxde?

---

### Post by ukripper on 2009-11-30
> **Zenith88 said:**
> Can I still run gnome applications such as Audacity under lxde?

yes. [http://lxde.org/lxde](http://lxde.org/lxde)

---

