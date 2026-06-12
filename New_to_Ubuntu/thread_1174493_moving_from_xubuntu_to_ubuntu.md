---
title: "moving from xubuntu to ubuntu"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by rsainath on 2009-05-31
Greetings from a newest Ubuntu rookie to the seasoned experts !! I just installed ubuntu into my machine that earlier had xubuntu. Then why is it that when I reboot, it launches xubuntu and not ubuntu ? I tried rebooting a few times same thing over and over !!
Thanks people !!:) Also is there a "Thank you" icon instead of the smile on the left ? Thanks.

---

### Post by superprash2003 on 2009-05-31
did you format the partition which had xubuntu earlier? you probably would have not completely remove xubuntu

---

### Post by rsainath on 2009-05-31
No I did not do any partitioning. Kindly guide me, should I do a complete reinstall of Ubuntu from the Ubuntu install CD? Thanks.

---

### Post by freeman2000 on 2009-05-31
Usually this happens because when you installed Ubuntu, you left Xubuntu on the computer, and during the installation it asked for a default OS and you might have stated Xubuntu.  Don't worry.  When it installs and gets to the splash screen, before you input your username and password, just click on options and change it to Ubuntu for login.  Once you login it will ask you if you just want Ubuntu for this session or as default.  Make your choice for default OS then.  Good luck.

---

### Post by superprash2003 on 2009-05-31
how many hard drives have you connected to this pc??

---

### Post by rsainath on 2009-06-05
> **freeman2000 said:**
> Usually this happens because when you installed Ubuntu, you left Xubuntu on the computer, and during the installation it asked for a default OS and you might have stated Xubuntu.  Don't worry.  When it installs and gets to the splash screen, before you input your username and password, just click on options and change it to Ubuntu for login.  Once you login it will ask you if you just want Ubuntu for this session or as default.  Make your choice for default OS then.  Good luck.
Not able to do this!! What am I doing wrong ??
Here's what I'm getting when I "sudo" via the terminal:
==============================================
[sudo] password for rsainath: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Windows
sudo apt-get install Ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Ubuntu

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Windows

sudo apt-get install Ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Ubuntu
===============================
I thought I did everything "by the book" or did I? LOL
Thanks people !!

---

### Post by linuxfreak1996 on 2009-06-05
Try this in the terminal.
```
sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins app-install-data-commercial aumix catfish cupsys-driver-gutenprint exo-utils fortune-mod fortunes-min gigolo gnumeric gnumeric-common gnumeric-doc gnumeric-gtk gpicview gtk2-engines-xfce imagemagick imagemagick-doc latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libdiscid0 libexo-0.3-0 libfftw3-3 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libmad0 libmpcdec3 libnotify-bin libofa0 libots0 librecode0 libt1-5 libtagc0 libthunar-vfs-1-2 libtunepimp5 libwv-1.2-3 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4 libxfconf-0-2 link-grammar-dictionaries-en listen mousepad mozilla-thunderbird orage oss-compat psutils python-gnome2-extras python-musicbrainz2 python-mutagen python-ogg python-pymad python-pyogg python-pysqlite2 python-pyvorbis python-tunepimp scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl8.4 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xubuntu-artwork xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```

---

