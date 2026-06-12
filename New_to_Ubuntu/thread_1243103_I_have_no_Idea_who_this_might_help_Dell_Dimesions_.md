---
title: "I have no Idea who this might help Dell Dimesions E531"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by R_W322 on 2009-08-17
Alright, I started my first linux adminstators jobs today and had to install Ubuntu 9.04 on a Dell Dimensions E531 /nVidia Geforce 6 series. 

I noticed quite a few post around google on help for installing on this particular machine so I figured I'd post what I did to get Ubuntu 9.04 on one these.

First download a copy of Xubuntu 9.04 then do a clean install of that and download all the upgrades and restart after the restart it should load into a blank screen "blue background with just a pointer" Hit Alt-F2 and instert this code ```
sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins app-install-data-commercial aumix catfish cupsys-driver-gutenprint exo-utils fortune-mod fortunes-min gigolo gnumeric gnumeric-common gnumeric-doc gnumeric-gtk gpicview gtk2-engines-xfce imagemagick imagemagick-doc latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libdiscid0 libexo-0.3-0 libfftw3-3 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libmad0 libmpcdec3 libnotify-bin libofa0 libots0 librecode0 libt1-5 libtagc0 libthunar-vfs-1-2 libtunepimp5 libwv-1.2-3 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4 libxfconf-0-2 link-grammar-dictionaries-en listen mousepad mozilla-thunderbird orage oss-compat psutils python-gnome2-extras python-musicbrainz2 python-mutagen python-ogg python-pymad python-pyogg python-pysqlite2 python-pyvorbis python-tunepimp scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl8.4 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xubuntu-artwork xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
``` then restart and boot into ubuntu and install the nvidia drivers after you've installed the upgrades on Xubuntu works great just though i'd pass this along to anyone having trouble with the Dell Demesions E5Series/nVidia

RYAN.WDZIECZNY

---

