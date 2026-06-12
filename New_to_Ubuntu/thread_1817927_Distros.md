---
title: "Distros?"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by Pyprokid on 2011-08-04
Hello,

I am rather new to Ubuntu, about a few weeks old using it, and I am unsure what the different Distro's of Ubuntu do. In fact, I am unsure what Disto I am using... I think it's Natty Narwhale. I could be wrong. 

Anybody who would like to take time out of their day to explain something I should probably already know please know, I appreciate it. :D

Respectfully,
Matt

---

### Post by bodhi.zazen on 2011-08-04
See :

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The versions are, in general, sorted by the default window manager.

Ubuntu = gnome
Kubuntu = KDE
Xubuntu = xfce
Lubuntu = LXDE

If you do not know what a window manager / DE is see

[http://xwinman.org/](http://xwinman.org/)

Ubuntu is released every 6 months.

See also : [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

To see what release you are running 

```
cat /etc/issue
```

---

### Post by Pyprokid on 2011-08-04
> **bodhi.zazen said:**
> See :

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The versions are, in general, sorted by the default window manager.

Ubuntu = gnome
Kubuntu = KDE
Xubuntu = xfce
Lubuntu = LXDE

If you do not know what a window manager / DE is see

[http://xwinman.org/](http://xwinman.org/)

Ubuntu is released every 6 months.

See also : [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

To see what release you are running 

```
cat /etc/issue
```

Thanks alot for your help! ^_^
I got:

Ubuntu 11.04 \n \l

After I ran it... what does \n \l mean?

---

### Post by pjd99 on 2011-08-04
Natty Narwhal is the alliterative name given to this **release** of Ubuntu. Ubuntu itself is the **distribution**. A Linux distribution uses the Linux kernel and a set of software tools, and will supply a desktop environment. eg, Ubuntu uses Gnome/Unity, Kubuntu uses KDE, Xubuntu uses XFCE, etc.

Examples of other **distributions** are Debian (which is what all the different flavours of *buntu are based on) and Fedora (community version of Red Hat Linux, which uses .rpm instead of .deb software packages).

11.04 -> Released April 2011. Normal release, so may contain a few bugs (esp 11.04 as it has a new Desktop Environment), but should also have lots of features and support for newer hardware.

LTS -> Long Term Support. These releases are designed to be more stable than the normal 6-month releases. Software for LTS releases is maintained for a longer period of time. Use an LTS release if you are looking for a rock-solid system.

Oneiric Ocelot is the name given to Ubuntu 11.10, which is scheduled for release in October this year. If you look through the names, you'll see that from 6.06 (Dapper Drake) that the alliterative name also goes up by a letter per release (eg. Edgy Eft, Feisty Fawn, Gutsy Gibbon etc).

---

### Post by Pyprokid on 2011-08-04
> **pjd99 said:**
> Natty Narwhal is the alliterative name given to this **release** of Ubuntu. Ubuntu itself is the **distribution**. A Linux distribution uses the Linux kernel and a set of software tools, and will supply a desktop environment. eg, Ubuntu uses Gnome/Unity, Kubuntu uses KDE, Xubuntu uses XFCE, etc.

Examples of other **distributions** are Debian (which is what all the different flavours of *buntu are based on) and Fedora (community version of Red Hat Linux, which uses .rpm instead of .deb software packages).

11.04 -> Released April 2011. Normal release, so may contain a few bugs (esp 11.04 as it has a new Desktop Environment), but should also have lots of features and support for newer hardware.

LTS -> Long Term Support. These releases are designed to be more stable than the normal 6-month releases. Software for LTS releases is maintained for a longer period of time. Use an LTS release if you are looking for a rock-solid system.

Oneiric Ocelot is the name given to Ubuntu 11.10, which is scheduled for release in October this year. If you look through the names, you'll see that from 6.06 (Dapper Drake) that the alliterative name also goes up by a letter per release (eg. Edgy Eft, Feisty Fawn, Gutsy Gibbon etc).

Ah thanks. That cleared up alot of questions I had. :D

---

