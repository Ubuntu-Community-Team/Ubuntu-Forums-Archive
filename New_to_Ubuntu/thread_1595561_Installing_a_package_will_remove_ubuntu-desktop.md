---
title: "Installing a package will remove ubuntu-desktop"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Pharod on 2010-10-13
I'm trying to get sound on a couple of games I run on Linux, but both fixes I have found will remove some pulseaudio package and the ubuntu-desktop package.

I don't want to continue installation because I don't know what could happen by doing this (the laptop works fine except for sound on those games).

If I remove the packages, to restore the previous state I would just remove the new ones and install the old ones?

Thanks for your help.

---

### Post by Quackers on 2010-10-13
I wouldn't recommend removing ubuntu-desktop. Things don't go well without it :-)

---

### Post by endotherm on 2010-10-13
well, to set your mind at ease a little, you can always reinstall all the packages under the "ubuntu-desktop" meta package with this line:
```
sudo apt-get install ubuntu-desktop
```

removing the metapackage isn;t a huge deal, but it does mess with some update/upgrade operations. never try a dist upgrade for instance on a system like that. you may also miss out on some application upgrades refered to by packages that have themselves been removed.

---

### Post by Pharod on 2010-10-13
Alright thanks. I think I'll play without sound for a while. I just don't get why would that package be removed. These are the two commands I try and what it says:

```
sudo apt-get install esound
The following packages will be REMOVED:
  pulseaudio-esound-compat ubuntu-desktop
The following NEW packages will be installed:
  esound

```
```
sudo apt-get install libsdl1.2debian-alsa
The following packages will be REMOVED:
  libsdl1.2debian-pulseaudio ubuntu-desktop
The following NEW packages will be installed:
  libsdl1.2debian-alsa

```

---

### Post by oldos2er on 2010-10-13
You can remove ubuntu-desktop, if need be; It's just a meta-package that doesn't affect anything. The only time you might need it is when running an upgrade to a new Ubuntu version.

---

### Post by Quackers on 2010-10-13
> **oldos2er said:**
> You can remove ubuntu-desktop, if need be; It's just a meta-package that doesn't affect anything. The only time you might need it is when running an upgrade to a new Ubuntu version.

For my peace of mind, when I mistakenly uninstalled evolution it removed ubuntu-desktop with it. This left my system with no GUI. My way out of this situation was to re-install ubuntu-desktop. This fixed it. So, was the loss of my GUI due to ubuntu-desktop's removal or not? :confused:

---

### Post by Pharod on 2010-10-13
Thanks for the help. :)

---

### Post by endotherm on 2010-10-13
> **Quackers said:**
> For my peace of mind, when I mistakenly uninstalled evolution it removed ubuntu-desktop with it. This left my system with no GUI. My way out of this situation was to re-install ubuntu-desktop. This fixed it. So, was the loss of my GUI due to ubuntu-desktop's removal or not? :confused:
in older versions of ubuntu, ubuntu-desktop had a "Depends" dependency for evolution, and gnome depended on evolution. in the newer versions, ubuntu-desktop and gnome-desktop "recommend" evolution, but do not "depend" on it.

---

### Post by mcduck on 2010-10-13
> **Quackers said:**
> For my peace of mind, when I mistakenly uninstalled evolution it removed ubuntu-desktop with it. This left my system with no GUI. My way out of this situation was to re-install ubuntu-desktop. This fixed it. So, was the loss of my GUI due to ubuntu-desktop's removal or not? :confused:

More likely you actually removed some Evolution components, which some Gnome components depend on and *that's* why you were left with no working desktop. ;)

At least gnome-panel has some evolution component on it's dependency list, the clock applet's popup menu shows evolution tasks & calender.

Removing the ubuntu-desktop metapackage is safe, the nly thing is that it should be reinstalled before upgrading to new Ubuntu release.

---

### Post by Quackers on 2010-10-13
Thanks for the info endotherm and mcduck (my long-lost cousin :-) ) that eases my mind.

---

### Post by Rubi1200 on 2010-10-13
I can confirm what both endotherm and mcduck have said; it is safe to remove the ubuntu-desktop metapackage (not forgetting to reinstall before an upgrade as pointed out).

In your case Quackers, I think what may have happened is that you removed the evolution-data-server package. And that, as you saw, can wreak havoc!

---

### Post by Quackers on 2010-10-13
I almost certainly removed everything connected with evolution. I'm nothing if not thorough :-)
And it did have dire consequences :-(
Today has been a learning day :-)

---

### Post by oldos2er on 2010-10-13
> **Quackers said:**
> For my peace of mind, when I mistakenly uninstalled evolution it removed ubuntu-desktop with it. This left my system with no GUI. My way out of this situation was to re-install ubuntu-desktop. This fixed it. So, was the loss of my GUI due to ubuntu-desktop's removal or not? :confused:

Without knowing what other packages were involved? I won't hazard a guess. My GUI works just fine without ubuntu-desktop installed.

---

