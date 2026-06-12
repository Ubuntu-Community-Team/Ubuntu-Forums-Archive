---
title: "unable to install gnome on KDE stange errors."
date: 2010-09-10
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-09-10
```
ubuntu-desktop:
 Depends: gdebi but it is not going to be installed
 Depends: gnome-themes-selected but it is not going to be installed
 Depends: gnome-themes-ubuntu but it is not going to be installed
 Depends: gtk2-engines-pixbuf but it is not going to be installed
 Depends: language-selector but it is not going to be installed
 Depends: libsdl1.2debian-pulseaudio but it is not going to be installed
 Depends: update-manager but it is not going to be installed
 Depends: update-notifier but it is not going to be installed
 Recommends: f-spot but it is not going to be installed
 Recommends: gnome-orca but it is not going to be installed
 Recommends: gvfs-fuse but it is not going to be installed
 Recommends: jockey-gtk but it is not going to be installed
 Recommends: libgail-gnome-module but it is not going to be installed
 Recommends: usb-creator-gtk but it is not going to be installed

```

Am i missing some software sources? im not sure what im ment to do, i really want gnome back so i will be able to mount my ipod, KDE doesn't seem to pick up ipods :(

---

### Post by zvacet on 2010-09-12
```
sudo apt-get install ubunntu-desktop
```

or

```
sudo tasksel install ubuntu-desktop
```

should install it.If you want to remove KDE and install Gnome see [this.]("http://psychocats.s465.sureserver.com/ubuntu/puregnome")

---

