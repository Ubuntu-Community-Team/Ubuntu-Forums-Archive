---
title: "Animated skydome glitches"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by SentientFluid on 2009-02-16
Hey all, I recently removed Kubuntu and went to a Pure Gnome system using [Psychocats instructions]("http://www.psychocats.net/ubuntu/puregnome").  Before doing so, animated skydome's worked perfectly.  After that it glitches like crazy.  The skydome works fine if it's not animated, but as soon as I animate it it looks like this:

[IMG]http://img.photobucket.com/albums/v19/SentientFluid/badskydome.png[/IMG]

What was removed in the code below that caused this, or what can I do to correct it?
```
sudo aptitude remove adept akregator amarok amarok-common amarok-engine-xine apport-qt ark dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3 libflac++6 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4 libkdepim4 libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4 libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libokularcore1 libphonon4 libplasma2 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0 libruby1.8 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxvmc1 libzip1 mediamanager mysql-common network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme phonon phonon-backend-gstreamer phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess python-kde4 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 qt4-qtconfig raptor-utils redland-utils ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dustin update-manager-kde update-notifier-kde
```

---

### Post by durand on 2009-02-16
Wow, thats a funky effect! It's pretty hard to say really. Your best bet is to reinstall the libraries and anything that doesn't look kde related in that list of programs.

---

### Post by SentientFluid on 2009-02-16
> **durand said:**
> Wow, thats a funky effect! It's pretty hard to say really. Your best bet is to reinstall the libraries and anything that doesn't look kde related in that list of programs.

Any ideas what the best way to go about that is? :)

---

### Post by RomeReactor on 2009-02-16
No idea why it's doing that, but you if you have Compiz Config Settings Manager installed you might want to reset the settings there (in CCSM go to Preferences and press 'Reset to defaults') to see if that helps.

---

### Post by jjblackfox on 2009-02-16
This happens to me if I use a skydome that is very graphically intense. Try using a lower resolution skydome and see if the problem still exits.

---

### Post by durand on 2009-02-17
Well, I personally would just reinstall all those programs and then remove the kde ones that you don't like. It wouldn't really hurt to keep them aside from taking up disk space.

---

### Post by SentientFluid on 2009-02-20
> **RomeReactor said:**
> No idea why it's doing that, but you if you have Compiz Config Settings Manager installed you might want to reset the settings there (in CCSM go to Preferences and press 'Reset to defaults') to see if that helps.

I tried reloading the Window Manager, still glitched.
I tried restarting, still glitched.
I disabled proprietary video drivers, restarted, reenable them, still glitched.
So I saved my CCSM profile and reset it to defaults and no glitch!

Funny thing, though... when I imported my profile back into CCSM without any changes, it was still working normally!

Thanks for the idea, Rome! :)

---

