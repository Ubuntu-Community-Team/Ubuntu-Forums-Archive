---
title: "Removing Kubuntu and Xubuntu"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by elurban3d on 2009-09-29
I am planning to separately install kubuntu and xubuntu as stand alone OSs.  Currently have only ubuntu installed.  If after tinkering with them I want to uninstall them, how do I do that so the system is restored as if I never installed either?

---

### Post by halitech on 2009-09-29
why not install the desktop environments in Ubuntu and choose between them at login? that way if you don't like them, you simply remove the ones you don't like.

```
sudo apt-get install kubuntu-desktop xubuntu-desktop
```

---

### Post by elurban3d on 2009-09-29
I just want to make sure that if I need to uninstall one of them, I have not created any issues with the ubuntu install.

---

### Post by wojox on 2009-09-29
No issues I've done the same before trying stuff out. After you install the desktops, reboot and at the login screen choose options > sessions and pick you DE of choice.

Then when you want to get rid of them just remove which ever.

---

### Post by zeroseven0183 on 2009-09-30
You can remove Xubuntu and all the packages with it in the Terminal.

```
sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins app-install-data-commercial aumix catfish cupsys-driver-gutenprint exo-utils fortune-mod fortunes-min gigolo gnumeric gnumeric-common gnumeric-doc gnumeric-gtk gpicview gtk2-engines-xfce imagemagick imagemagick-doc latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libdiscid0 libexo-0.3-0 libfftw3-3 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libmad0 libmpcdec3 libnotify-bin libofa0 libots0 librecode0 libt1-5 libtagc0 libthunar-vfs-1-2 libtunepimp5 libwv-1.2-3 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4 libxfconf-0-2 link-grammar-dictionaries-en listen mousepad mozilla-thunderbird orage oss-compat psutils python-gnome2-extras python-musicbrainz2 python-mutagen python-ogg python-pymad python-pyogg python-pysqlite2 python-pyvorbis python-tunepimp scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl8.4 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xubuntu-artwork xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs
```But like them (above), I would suggest you keep them then just log-off to select a new session. I have no problem with that.

I'm switching DEs - GNOME, Lxde and Xfce.

---

