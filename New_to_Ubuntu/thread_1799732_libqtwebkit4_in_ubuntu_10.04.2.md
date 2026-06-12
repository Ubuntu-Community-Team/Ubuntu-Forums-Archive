---
title: "libqtwebkit4 in ubuntu 10.04.2"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by owiknowi on 2011-07-08
hi everyone,

os: ubuntu 10.04.2
need: libqtwebkit4 (required by a new to install application)

does anyone know if it's possible to install libqtwebkit4 in 10.04.2 without leaving the os unstable or having to upgrade to a non-lts version?

thanks for any help!

---

### Post by nomko on 2011-07-08
I've had the ssame issue months ago when i installed a program which also required the libqtwebkit4 package. The only way to get this package is adding the kubuntu backport in your sources.list (or software source). You can find it here: [https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)
 
Please be aware that if you add this in Ubuntu (with Gnome) that some KDE packages will be updated or has to be updated in order to get them working properly again. The new package libqtwebkit4 will update some KDE packages which has impact on already installed KDE applications.
 
You can read about backports here: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by owiknowi on 2011-07-08
@nomko

thanks, nomko.
it looks like it worked after adding ppa:kubuntu-ppa/backports to the list of repositories.

don't know how (un)stable u10.04.2 is after this installation since there were rather a few extra kde packages installed due to dependencies.
no doubt i'll find out in due time ;)

---

### Post by nomko on 2011-07-08
So far i haven't encounter any problems after adding the kubuntu backport ppa. The only thing which could effect your system is that you migth have to update some KDE programs like K3B.

---

### Post by owiknowi on 2011-07-08
i agree, nomko: did the same install again with a clean u10.04.2 and that seems to keep running smooth. the application runs smooth too.

the first time used a installation where i installed k3b in ubuntu and that came with a lot of dependences.
with the latter i even had a second package update applet (kpakagekit) which did not quite seem to agree with the default gnome update applet.

thanks again!

---

