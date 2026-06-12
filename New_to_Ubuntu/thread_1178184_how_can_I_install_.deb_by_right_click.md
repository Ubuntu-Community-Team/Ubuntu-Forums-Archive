---
title: "how can I install .deb by right click?"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by colormoon on 2009-06-04
Hi there,
I wanna know what package to install .deb by right click?
thank you,

---

### Post by nandemonai on 2009-06-04
What Desktop Environment? In Gnome the first option 'Open with GDebi Package Installer' does the trick here.

You can always install from terminal like so:

```
sudo dpkg -i packagename.deb
```

---

### Post by Tibuda on 2009-06-04
Right-click? You can install packages by double-click using GDebi. It's installed by default in Ubuntu, not sure about Xubuntu. If it is not, try installing the gdebi package.

---

### Post by clive littlewood on 2009-06-04
Hi

.deb files are installed by double left click.

They will be installed and a menu item placed in the correct menu. They usually will then appear in Add/Remove so you can uninstall if required

Clive

---

### Post by colormoon on 2009-06-04
Thank you,
I install xubuntu in command line and install every package by myself. I use xfce desktop environment and I want my system will more lightweight than default xubuntu. So I will try gdebi.

---

### Post by x33a on 2009-06-04
you can use gdebi from the commandline also.
```
sudo gdebi package.deb
```

it's better than dpkg, since it resolves the dependencies as well.

---

### Post by nandemonai on 2009-06-05
> **x33a said:**
> you can use gdebi from the commandline also.
```
sudo gdebi package.deb
```

it's better than dpkg, since it resolves the dependencies as well.

Duely noted ;) I didn't realise gdebi actually resolved dependencies. Handy indeed.

---

### Post by anjilslaire on 2009-06-05
I run Xubuntu 8.10, with gdebi installed. I can right-click and do "Open With GDebi Package Installer"

Works well.

---

### Post by Paqman on 2009-06-05
> **nandemonai said:**
> Duely noted ;) I didn't realise gdebi actually resolved dependencies. Handy indeed.

It's not so much gdebi as it is the underlying package management system, APT. Synaptic, apt-get, aptitude, gdebi etc are all just different ways of working with APT.

---

### Post by nandemonai on 2009-06-05
> **Paqman said:**
> It's not so much gdebi as it is the underlying package management system, APT. Synaptic, apt-get, aptitude, gdebi etc are all just different ways of working with APT.

I actually always assumed gdebi was actually a front end to dpkg. Learn something new every day huh? :) Cheers for clearing that up.

---

### Post by kerry_s on 2009-06-05
or you could just do a custom launcher

**xfterm4 -e sudo dpkg -i %f**

---

