---
title: "Dependency Error"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by Warpnow on 2010-05-21
First time toying with KDE/Qt. Still using jaunty because its on a netbook where Jaunty works out of the box but Karmic/Lucid don't.

Can someone help me figure out why I get this?

> 

chase@chase-laptop:~/Downloads/systester-1-src/systester-1.1.0-src$ sudo apt-get install libqt4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-dev: Depends: libqt4-dbus (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-qt3support (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-xml (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqtcore4 (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqtgui4 (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-network (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-svg (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-webkit (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-sql (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-script (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-scripttools (= 4.5.0-0ubuntu4.3) but it is not going to be installed
              Depends: libqt4-xmlpatterns (= 4.5.0-0ubuntu4.3) but it is not going to be installed
              Depends: libqt4-designer (= 4.5.0-0ubuntu4.3) but 4.5.2-0ubuntu2~jaunty1~ppa2 is to be installed
              Depends: libqt4-help (= 4.5.0-0ubuntu4.3) but it is not going to be installed
              Depends: libqt4-assistant (= 4.5.0-0ubuntu4.3) but it is not going to be installed
              Depends: libqt4-test (= 4.5.0-0ubuntu4.3) but it is not going to be installed
              Recommends: libqt4-opengl-dev (= 4.5.0-0ubuntu4.3) but it is not going to be installed
E: Broken packages


---

### Post by -humanaut- on 2010-05-21
Looks like you need to find a more up-to-date PPA check kubuntu.org theres a new dev kit on there with the right PPA to add.

---

### Post by lanetherif on 2010-05-21
> **Warpnow said:**
> First time toying with KDE/Qt. Still using jaunty because its on a netbook where Jaunty works out of the box but Karmic/Lucid don't.

Can someone help me figure out why I get this?

It might sound daft or obvious, still I will utter. :P Have you tried using dkpg in start-up (shift+r thing) for broken packages?

---

### Post by Chesamo on 2010-05-21
sudo apt-get -f install

---

### Post by Warpnow on 2010-05-21
I have the Kubuntu PPA, and apt-get -f install doesn't do anything...

No idea what to do. Not a good first start for KDE for me. ;)

---

### Post by Warpnow on 2010-05-21
In case anyone finds this thread with a similar problem the solution was to install the mentioned packages at the exact version  required. Like sudo apt-get install PACKAGE== 4.5.0-0ubuntu4.3

The problem was TOO up to date packages. Had to downgrade them.

---

