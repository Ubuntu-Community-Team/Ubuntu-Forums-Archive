---
title: "question about  compiz upgrade 0.8.4 to 0.9.0 ubuntu lucid"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by Tracy177 on 2010-09-01
hi i found i can upgrade compiz so i would like to to that on ubuntu 10.04 

i got git repistory 
sudo add-apt-repository ppa:falk-t-j/lucid-latest

and why i try to 
sudo apt-get install compiz-git

i get a lot of new packages like kde etc etc etc is this normal ? i use gnome and dont want to brake something and have problem booting ubuntu so what do you guys think ????

sudo apt-get install compiz-git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  exiv2 gdebi-kde icoutils install-package kdebase-runtime
  kdebase-runtime-data kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs-data
  kdepimlibs5 kdesudo kpackagekit kubuntu-debug-installer libakonadiprivate1
  libattica0 libboost-program-options1.40.0 libboost-serialization1.40.0
  libclucene0ldbl libdbusmenu-qt2 libexiv2-6 libiodbc2 libkdecorations4
  libmysqlclient16 libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4
  libplasma3 libpolkit-qt-1-0 libqca2 libqt4-assistant libqt4-dbus
  libqt4-designer libqt4-help libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test
  libqt4-webkit libqt4-xml libqt4-xmlpatterns libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libx11-xcb1 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x mysql-common oxygen-icon-theme packagekit packagekit-backend-apt
  phonon phonon-backend-xine plasma-scriptengine-javascript polkit-kde-1
  python-kde4 python-packagekit python-qt4 python-sip
  shared-desktop-ontologies software-properties-kde soprano-daemon ttf-dejavu
  update-manager-kde virtuoso-nepomuk
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl djvulibre-bin hspell
  akonadi-server libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg
  libqca2-plugin-ossl libqca2-plugin-pkcs11 libqt4-dev gxine xine-ui
  libxine1-doc libxine-doc libxine1-ffmpeg phonon-backend-gstreamer
  phonon-backend-vlc phonon-backend-mplayer kcm-phonon-xine python-qt4-dbg
The following NEW packages will be installed
  compiz-git exiv2 gdebi-kde icoutils install-package kdebase-runtime
  kdebase-runtime-data kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs-data
  kdepimlibs5 kdesudo kpackagekit kubuntu-debug-installer libakonadiprivate1
  libattica0 libboost-program-options1.40.0 libboost-serialization1.40.0
  libclucene0ldbl libdbusmenu-qt2 libexiv2-6 libiodbc2 libkdecorations4
  libmysqlclient16 libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4
  libplasma3 libpolkit-qt-1-0 libqca2 libqt4-assistant libqt4-dbus
  libqt4-designer libqt4-help libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test
  libqt4-webkit libqt4-xml libqt4-xmlpatterns libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libx11-xcb1 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x mysql-common oxygen-icon-theme packagekit packagekit-backend-apt
  phonon phonon-backend-xine plasma-scriptengine-javascript polkit-kde-1
  python-kde4 python-packagekit python-qt4 python-sip
  shared-desktop-ontologies software-properties-kde soprano-daemon ttf-dejavu
  update-manager-kde virtuoso-nepomuk
0 upgraded, 76 newly installed, 0 to remove and 40 not upgraded.
Need to get 81.0MB of archives.
After this operation, 283MB of additional disk space will be used.
Do you want to continue [Y/n]?


should i install it or not ?

---

### Post by andrewthomas on 2010-09-01
No, try this one

 [https://launchpad.net/~compiz/+archive/ppa]("https://launchpad.net/%7Ecompiz/+archive/ppa")

```
deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) lucid main
```

**ppa:compiz/ppa**

---

### Post by Tracy177 on 2010-09-02
> **andrewthomas said:**
> No, try this one

 [https://launchpad.net/~compiz/+archive/ppa]("https://launchpad.net/%7Ecompiz/+archive/ppa")

```
deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) lucid main
```**ppa:compiz/ppa**


yup i did it upgraded to 0.8.6 and been asking people on the  #compiz found 0.9.0 isnt stable so i wont even try to install it maybe next month or something :)

tnx

---

