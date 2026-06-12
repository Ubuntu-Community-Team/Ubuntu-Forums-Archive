---
title: "Tried Xubuntu, didn't like, how to remove?"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by Carborundum on 2011-05-06
I installed Xubuntu alongside Ubuntu to see if the increase in speed was worth sacrificing Unity. I decided it wasn't.

What is the easiest way to reclaim the space alloted to Xubuntu, and re-extend the Ubuntu partition into it? I realize I could create a LiveUSB with PartedMagic, but is there anyway to do it from inside the OS?

---

### Post by dniMretsaM on 2011-05-06
```
 sudo apt-get remove a2ps abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview browser-plugin-parole catfish   elementary-icon-theme exo-utils gigolo gimp gimp-data gmusicbrowser gnome-time-admin gnumeric gnumeric-common gnumeric-doc   gtk2-engines-xfce gvfs-bin libabiword-2.8 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a   libao-common libao4 libasyncns0 libaudio-scrobbler-perl libbabl-0.0-0 libclutter-1.0-0 libclutter-1.0-common   libclutter-gtk-0.10-0 libconfig-inifiles-perl libexo-1-0 libexo-common libgarcon-1-0 libgarcon-common libgdome2-0   libgdome2-cpp-smart0c2a libgegl-0.0-0 libgimp2.0 libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114 libgsf-1-common   libgstreamer-perl libgtk2-notify-perl libgtk2-trayicon-perl libgtkmathview0c2a libid3tag0 libilmbase6 libjpeg-progs   libjpeg8 libkeybinder0 liblink-grammar4 libloudmouth1-0 libmad0 libmng1 libopenexr6 libotr2 libots0 libsexy2 libtagc0   libthunarx-2-0 libtumbler-1-0 libwv-1.2-3 libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfcegui4-4   libxfconf-0-2 link-grammar-dictionaries-en mousepad mpg321 murrine-themes orage parole pidgin pidgin-data pidgin-libnotify   pidgin-otr plymouth-theme-xubuntu-logo plymouth-theme-xubuntu-text psutils quadrapassel ristretto tango-icon-theme   tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman thunderbird   thunderbird-globalmenu ttf-droid ttf-lyx tumbler tumbler-common wdiff xchat xchat-common xfburn xfce-keyboard-shortcuts   xfce4-appfinder xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-indicator-plugin xfce4-mailwatch-plugin   xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel   xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings   xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin   xfce4-volumed xfce4-weather-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xscreensaver   xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-gdm-theme xubuntu-icon-theme   xubuntu-wallpapers && sudo apt-get install ubuntu-desktop
```
That should do it.

---

### Post by techunit on 2011-05-06
```
sudo apt-get purge xubuntu-desktop
```
should be run from Ubuntu this will remove alot so be warned.

---

### Post by adit on 2011-05-06
To the users who posted post#2 and post#3:
He has installed xubuntu in a *separate partition*.  He is asking how to delete the partition and resize ubuntu partition.  He also wants to resize from within ubuntu (not from a live cd)

---

### Post by Carborundum on 2011-05-06
> **adit said:**
> He has installed xubuntu in a *separate partition*.  He is asking how to delete the partition and resize ubuntu partition.  He also wants to everything from within ubuntu (not from a live cd)
Yes, thank you for clarifying this for me. I wanted to test boot-time, among other things, so I had to create a separate partition.

---

### Post by dniMretsaM on 2011-05-06
Use GParted to delete the Xubuntu partition and then resize the Ubuntu one. Install GParted by running
```
sudo apt-get install gparted
```Run it with ```
sudo gparted
```Or you can find it in the application menu (If you ever want to use it in Classic, it's in System -> Administration).

> **techunit said:**
> ```
sudo apt-get purge  xubuntu-desktop
```should be run from Ubuntu this will remove alot so  be warned.

Will that actually delete it? I thought that xubuntu-desktop was a  metapackage which means it won't delete everything. Does purge work  differently that apt-get remove? Just wondering.

---

### Post by Carborundum on 2011-05-06
> **dniMretsaM said:**
> Use GParted to delete the Xubuntu partition and then resize the Ubuntu one. Install GParted by running
```
sudo apt-get install gparted
```Run it with ```
sudo gparted
```Or you can find it in the application menu (If you ever want to use it in Classic, it's in System -> Administration).
GParted won't let me resize the Ubuntu partition while it is mounted.

---

### Post by laithbsoul on 2011-05-06
to re size your Ubuntu partition your gonna need to use either a live cd or usb

---

### Post by Carborundum on 2011-05-06
Well, I created a LiveUSB with PartedMAgic, and somehow managed to render my Ubuntu partition unbootable.

Whatever, I'll just save some documents and reinstall the entire thing. Should probably have done that to begin with anyway.

---

### Post by laithbsoul on 2011-05-06
you probably just need to reinstall grub because it was in the XUbuntu partition heres a thread that tells you how to reinstall grub [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) its under 13. Reinstalling GRUB 2 from the LiveCD

---

### Post by Carborundum on 2011-05-06
> **laithbsoul said:**
> you probably just need to reinstall grub because it was in the XUbuntu partition heres a thread that tells you how to reinstall grub [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) its under 13. Reinstalling GRUB 2 from the LiveCD
I'm already done reinstalling, but thanks anyway. I'll remember that next time I screw up my boot-loader. :D

---

