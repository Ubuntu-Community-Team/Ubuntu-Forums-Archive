---
title: "how to take Xfce off ubuntu?"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by ynnojC on 2010-03-31
I installed Xfce on ubuntu using : sudo aptitude update && sudo aptitude install xubuntu-desktop. How do i compleately take it off? There are alot of side effect such as there are 2 terminals in the menu.

---

### Post by sisco311 on 2010-03-31
[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by ynnojC on 2010-03-31
I used 
 sudo aptitude remove xubuntu-desktop, Xfce is gone, but there is still 2 terminals. Also, compiz doesn't start with Gnome. I have to go to terminal and type in compiz.:guitar:

---

### Post by halitech on 2010-03-31
per the link that sisco311 posted

> sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins app-install-data-commercial catfish exaile exo-utils feh fortune-mod fortunes-min giblib1 gigolo gnome-app-install gnumeric gnumeric-common gnumeric-doc gtk2-engines-xfce imagemagick libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgoffice-0-8 libgoffice-0-8-common libgtkmathview0c2a libid3tag0 libimlib2 liblink-grammar4 libotr2 libots0 libpolkit-dbus2 libpolkit-gnome0 libpolkit-grant2 libpolkit2 librecode0 libscim8c2a libt1-5 libtagc0 libthunar-vfs-1-2 libwv-1.2-3 libxcb-keysyms1 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4 libxfconf-0-2 libxmlrpc-core-c3 link-grammar-dictionaries-en mousepad orage pidgin pidgin-data pidgin-libnotify pidgin-otr policykit policykit-gnome psutils python-cddb python-mmkeys python-mutagen ristretto scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird ttf-arphic-uming ttf-liberation usb-creator usplash-theme-xubuntu vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xubuntu-artwork xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-gdm-theme xubuntu-wallpapers && sudo apt-get install ubuntu-desktop 

did you run that?

---

### Post by ynnojC on 2010-03-31
> **sisco311 said:**
> [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

thanks! im runing it right now, ill post again if it doesnt work.

---

### Post by ynnojC on 2010-03-31
everything worked, exept compiz still doesnt start with gnome. Even after i tell it to in startup apps. under command,i just typed in compiz, because that is what i type in terminal to start compiz. Is this the problem?

---

### Post by sisco311 on 2010-03-31
try:
```

gconftool-2 --set -t string /desktop/gnome/applications/window_manager/current /usr/bin/compiz
gconftool-2 --set -t string /desktop/gnome/applications/window_manager/default /usr/bin/compiz

```

---

### Post by ynnojC on 2010-03-31
Nope, sorry. I created a launcher on the desktop. Is there anyway i could make it start automaticly?

---

### Post by mechro on 2010-03-31
Have you set **System > Preferences > Appearance > Visual Effects**?

---

### Post by ynnojC on 2010-03-31
> **mechro said:**
> Have you set **System > Preferences > Appearance > Visual Effects**?

I use the advanced compiz manager, and if i use the settings you described, it will override mine.

---

### Post by ynnojC on 2010-03-31
> **halitech said:**
> per the link that sisco311 posted



did you run that?

yup, nuthin.

---

### Post by mechro on 2010-04-01
> **ynnojC said:**
> I use the advanced compiz manager, and if i use the settings you described, it will override mine.

Understood, but if Visual Effects are set to None, won't that override advanced compiz manager?

---

