---
title: "Why it is saying this you must manually run 'dpkg --configure -a' to correct the prob"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by brad_pitt on 2009-05-21
Hi All,

Recently i have installed KDE as mentioned in this link [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde) and today  i wanted to remove kde so i followed the instructions given in this page [http://www.psychocats.net/ubuntu/puregnomeintrepid ]("http://www.psychocats.net/ubuntu/puregnomeintrepid")

the first command i entered in the terminal was  
[html]<div class="terminal">sudo apt-get remove adept akregator amarok amarok-common amarok-engine-xine apport-qt ark dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3 libflac++6 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4 libkdepim4 libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4 libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libokularcore1 libphonon4 libplasma2 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0 libruby1.8 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxvmc1 libzip1 mediamanager mysql-common network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme phonon phonon-backend-gstreamer phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess python-kde4 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 qt4-qtconfig raptor-utils redland-utils ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dustin update-manager-kde update-notifier-kde && sudo apt-get install ubuntu-desktop</div>
[/html]

it started removing some packages but suddenly a pop up came that KDE is running one X server do u want to stop current X session something like that i dont remember exactly i said yes then suddenly my current desktop session terminated and a dos screen came up 

and the last statement there was checking current battery state   ....[OK]

it was idle for 20 min so i pressed ctrl+alt+del so machine restarted.

and now if i paste the same command in the terminal it is throwing the below error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

What did i do wrong.

Please help me..

I want to completely remove KDE.

Regards
Brad

---

### Post by apjone on 2009-05-21
This is because the uninstall was interrupted. You need to run 'dpkg --configure -a' so it can complete the process.
[COLOR="Red"]
You should run this from a Ctrl+Alt+F3 as it will likely restart X again due to whatyou are doing.

```
sudo dpkg --configure -a
```[/COLOR]

---

### Post by halitech on 2009-05-21
sounds like the removal didn't happen properly. Were you logged into the KDE desktop when you tried to remove it?

open a terminal and run
```
sudo dpkg --configure -a
```and that should take care of it for you

---

### Post by brad_pitt on 2009-05-21
Thanks guys.

I removed kubuntu successfully.

Regards
brad

---

