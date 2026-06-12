---
title: "need help uninstalling global menu"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by phandrew08 on 2009-01-18
I currently installed gnome-globalmenu-0.7.2-1.fc10.src.rpm  but i found out this version would not work on 8.10 i needed the version before that.

how do i uninstall gnome-globalmenu-0.7.2-1.fc10.src.rpm ?

---

### Post by jimmy the saint on 2009-01-18
How did you install the .rpm in the first place?  Ubuntu uses .deb packages, not .rpm

---

### Post by phandrew08 on 2009-01-18
i was able to do this because i used alien which converts rpm files to deb files.

---

### Post by mac71 on 2009-01-18
Here's a step by step to install the latest for ubuntu (working fine on my 8.10) and to uninstall.

[http://code.google.com/p/gnome2-globalmenu/wiki/BuildFromSource](http://code.google.com/p/gnome2-globalmenu/wiki/BuildFromSource)

---

### Post by jimmy the saint on 2009-01-18
If you isntalled it as a .deb it should show up as installed in synaptic package manager.  Just select it and choose "completely remove"

---

### Post by MenZa on 2009-01-18
Just a tip: Using alien is a terrible way of converting RPM packages and let them install on your system. There is **always** a better way; including compiling from source.

---

