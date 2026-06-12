---
title: "Xubuntu to Ubuntu Transition"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Elycian on 2008-12-07
Hey, I installed Xubuntu recently thinking it may be easier for my family and easier on the computer but it's been giving everyone a hard time.

Is there anyway I can install normal ubuntu along with xubuntu so I don't have to uninstall xubuntu and transfer everything? I think there's a way, but I'm not quite sure.
Thanks :]

---

### Post by Paqman on 2008-12-07
The only difference between Ubuntu and Xubuntu is the desktop environment.

To install Ubuntu install the package ubuntu-desktop. You'll then be able to pick Ubuntu's Gnome environment when you log in. If you want to ditch Xubuntu's XFCE desktop completely throw this into a terminal:
```
sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins aumix catfish cupsys-driver-gutenprint exo-utils gnumeric gnumeric-common gnumeric-gtk gpicview gtk2-engines-xfce imagemagick latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libdiscid0 libexo-0.3-0 libfftw3-3 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libmad0 libmpcdec3 libnotify-bin libofa0 libots0 libt1-5 libtagc0 libthunar-vfs-1-2 libtunepimp5 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 link-grammar-dictionaries-en listen mousepad mozilla-thunderbird orage psutils python-ctypes python-gnome2-extras python-musicbrainz2 python-mutagen python-ogg python-pymad python-pyogg python-pysqlite2 python-pyvorbis python-tunepimp scim-modules-table scim-tables-additional slocate tango-icon-theme tango-icon-theme-common tcl8.4 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-governor-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mcs-plugins-extra xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```

I find some parts of the Xubuntu envirnoment are worth hanging on to though; Abiword is IMO a much better word processor than Open Office Write, for example.

---

### Post by Elycian on 2008-12-13
Thanks, I already realized that, ubuntu is gnome and xubuntu is xfwm3 or something like that.. although I should've posted this as solved a long time ago.. my bad.

---

