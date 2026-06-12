---
title: "Gnome/KDE"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by Robert1305 on 2011-04-27
I am using Ubuntu 10.10, and really enjoying the experience.

What I would like to know, how can I change from using Gnome desktop to using KDE, I dont know if 10.10 comes with both at install.

Any help greatly appreciated. :D

---

### Post by kaldor on 2011-04-27
10.10 only has GNOME 2.32 by default. You may want to install Kubuntu, an Official KDE version of Ubuntu, instead.

If you want both GNOME and KDE as options, I'd install the kubuntu-desktop metapackage; it brings in all the programs and artwork related to Kubuntu. You can then choose GNOME or KDE whenever you are logging in.

To install, paste this in the Terminal:

```
sudo apt-get install kubuntu-desktop
```

Alternatively, you can search for Kubuntu Desktop in the Software Centre.

Have fun :)

Edit: Note that this is roughly 700mb to download. If you only want a minimal KDE install, try installing kde-standard or kde-minimal packages instead.

---

