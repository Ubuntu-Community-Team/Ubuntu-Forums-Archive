---
title: "remove distro"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by mayagrafix on 2009-01-03
I started with Gnome, then added Xfce and KDE. How do I remove KDE but keep Gnome and XFCE?

---

### Post by ken22 on 2009-01-03
```
sudo aptitude remove kubuntu-desktop
```

I believe that will do it.

Please read this [here]("http://www.tech-recipes.com/rx/2755/ubuntu_7_10_how_to_uninstall_kde/") too. It gives examples.

---

### Post by alienexplorers on 2009-01-03
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by civillian on 2009-01-03
A more thorough way is on [this bolg](http://httpwww.psychocats.net/ubuntu) and to get back to "pure gnome" they advise using the following commands

```
sudo apt-get remove adept akregator amarok amarok-common amarok-engine-xine apport-qt ark dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3 libflac++6 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4 libkdepim4 libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4 libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libokularcore1 libphonon4 libplasma2 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0 libruby1.8 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxvmc1 libzip1 mediamanager mysql-common network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme phonon phonon-backend-gstreamer phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess python-kde4 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 qt4-qtconfig raptor-utils redland-utils ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dustin update-manager-kde update-notifier-kde && sudo apt-get install ubuntu-desktop
```

which will remove some things that removing kubuntu-desktop doesn't remove, since kubuntu-desktop is only a meta package.

---

### Post by albinootje on 2009-01-03
> **mayagrafix said:**
> I started with Gnome, then added Xfce and KDE. How do I remove KDE but keep Gnome and XFCE?

That's not easy :|
Try removing all KDE based applications and libraries that you don't need.

(Removing the kubuntu-desktop meta-package is likely only gonna remove that one meta-package, and nothing more.)

---

### Post by mayagrafix on 2009-01-03
Thanks to everyone who replied. Considering that this is a test machine, I have the option of just re-formating and re-installing Ubuntu from the CD. Is this a good solution?

The reason I want to remove KDS is because I'm having problems with the Menu Panels in Xfce... the panels from Gnome appear over the Xfce ones when I log into the Xfce desktop. Everything seems to run fine, except for the over abundance of menu panels :o

---

### Post by albinootje on 2009-01-03
> **mayagrafix said:**
> Thanks to everyone who replied. Considering that this is a test machine, I have the option of just re-formating and re-installing Ubuntu from the CD. Is this a good solution?

Sure, but see below.
> 
The reason I want to remove KDS is because I'm having problems with the Menu Panels in Xfce... the panels from Gnome appear over the Xfce ones when I log into the Xfce desktop. Everything seems to run fine, except for the over abundance of menu panels :o

Instead of a reinstall, you can add a new user and see whether that helps.
It sounds like your "sessions" and user configuration is "just a little messed up".

---

### Post by mayagrafix on 2009-01-04
> Instead of a reinstall, you can add a new user and see whether that helps.
It sounds like your "sessions" and user configuration is "just a little messed up".

OK, I created a new user and that worked. Xfce is back to normal and Gnome works great also, the panels are back in their place. So what is my next step?

Is there a way to fix the user config file or should I just keep the two profiles?

---

