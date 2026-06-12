---
title: "[SOLVED] Upgrading 7.04 WUBI to a 8.10 'real' install"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by LeeHB on 2008-12-25
**Upgrading 7.04 WUBI to a 8.10 'real' install**

I've been using FEISTY for almost two years; it's doing everything that I need it to do and is running beautifully. No problem accessing any of my hardware, including another networked XP box and a networked printer. It is currently running under WUBI.

Obviously, it's no longer getting any updates or support. I'd like to upgrade to a 'real' install of INTREPID.

I have lots of programs and utilities installed; will all these have to be re-installed in 8.10??? Or is there an easy way to copy my current 7.04 WUBI installation and data files to the new 8.10 "real" install.

Thanx in advance from a 73 year old Ubuntu n00b...who's loving Linux...:)

LeeHB

---

### Post by namdung on 2008-12-25
Taken from
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[I]Upgrading from 7.04 to 7.10 is NOT supported, due to the fundamental differences between 7.04 and 7.10. The best route is to uninstall and install Wubi-8.10 (you can save the old installation files and access them from 8.10) or move your 7.04 installation to a dedicated partition via LVPM, then upgrade using the standard upgrade-manager tool.

Upgrading from 7.10 to 8.04 might work, but it has not been tested yet.

Upgrading from 8.04 to 8.10 is supported.[/I]

Wubi may have some performace issues and some features like hibernation may not work. I recommend u do a fresh install if possible. Hardy Heron LTS is recommended, the next version 8.04.2 which is out in Jan 09. Intrepid has more features but it also may have more bugs.

---

### Post by Elfy on 2008-12-25
As fara s I'm aware there is not directo update path from 7.04 to 8.10 now that 7.04 is out of support. Even if it was in support the upgrade path would have been 7.04 - 7.10 - 8.04 - 8.10

It's likely that your best option would be to do a clean install of 8.10 .

You need to ensure that you have backups of important data.

It might be better for you to install the 8.04LTS version - this is supported for much longer and, assuming things are equal, once the next LTS is released in a few years time you will have a direct upgrade route to it.

---

### Post by LeeHB on 2008-12-25
It looks like 8.04LTS is the way to go...

Thanx, all
LeeHB

---

