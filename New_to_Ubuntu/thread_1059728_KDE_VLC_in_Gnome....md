---
title: "KDE VLC in Gnome..."
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Muffinabus on 2009-02-04
I installed the kubuntu-desktop package a few days ago to try out KDE.  Didn't so much like what I saw, I'm more comfortable with Gnome, so I'm back!  But this is REALLY annoying me now.  When I installed the kubuntu-desktop, it replaced my normal VLC with a VLC that has KDE menus and whatnot, even while I'm in Gnome.  This is such a small problem, yet it's annoying the CRAP out of me and I feel like there is probably such a simple solution, something that I'm missing, to get it back to normal.

I've tried uninstalling, purging, and reinstalling, and nothing seems to work!  Any ideas?

Screenshot: [http://img.photobucket.com/albums/v109/tmm_xiv/kdevlc.jpg](http://img.photobucket.com/albums/v109/tmm_xiv/kdevlc.jpg)

---

### Post by lakersforce on 2009-02-04
If you really want to try kde, you should try out Kubuntu. Just as Gnome looks different when you install kde on the system, kde will look different if you install Kubuntu without Gnome on the system.

Try and search for kde packages installed (I bet you have some left) and uninstall them.

---

### Post by Muffinabus on 2009-02-04
> **lakersforce said:**
> If you really want to try kde, you should try out Kubuntu. Just as Gnome looks different when you install kde on the system, kde will look different if you install Kubuntu without Gnome on the system.

Try and search for kde packages installed (I bet you have some left) and uninstall them.

Have already done this:

```
sudo apt-get remove adept akregator amarok amarok-common amarok-engine-xine apport-qt ark dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3 libflac++6 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4 libkdepim4 libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4 libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libokularcore1 libphonon4 libplasma2 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0 libruby1.8 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxvmc1 libzip1 mediamanager mysql-common network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme phonon phonon-backend-gstreamer phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess python-kde4 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 qt4-qtconfig raptor-utils redland-utils ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dustin update-manager-kde update-notifier-kde
```

Then just reinstalled anything that was removed that I actually wanted.

---

### Post by lakersforce on 2009-02-04
Here's what I did (although I would like to see an answer to this question): Full reinstall.

---

### Post by Muffinabus on 2009-02-04
> **lakersforce said:**
> Here's what I did (although I would like to see an answer to this question): Full reinstall.

Hehe, yikes.  A bit too extreme just to change the look of my VLC back!  (Though it is bothering me... hmm)

---

