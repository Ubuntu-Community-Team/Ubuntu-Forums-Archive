---
title: "I'm getting an error when trying to remove KDE"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by PJOS13 on 2011-01-14
Hi, I'm trying to remove KDE, and I found in another thread that th method described here is the best: [http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

But when I run that in the terminal I get this error: 

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not going to be installed
E: Broken packages

```

any suggestions?

---

### Post by kindafunnylookin on 2011-01-14
no solution, just sympathy. I have the same problem and posted about a halfhour after you did. Good luck.

---

### Post by PJOS13 on 2011-01-14
Hope someone post an answer.

---

### Post by PJOS13 on 2011-01-15
how can I install those java packages too so that I don't get that error?

---

### Post by kindafunnylookin on 2011-01-15
I have no idea. I'm leaving KDE on as an option. I will follggow this thread though to see how it is done. If I get it I'll let you know.

---

### Post by PJOS13 on 2011-01-15
Thank you

---

### Post by HermanAB on 2011-01-16
Howdy,

You cannot unscramble an egg.

If you don't want KDE at all, re-install regular Ubuntu.  

However, why bother uninstalling it?  Just select Gnome as your default desktop when you log in if you don't like KDE.

---

### Post by PJOS13 on 2011-01-16
Ok, I'll keep KDE, but at least I want the ubuntu logo (not the kubuntu logo) back when the OS boots. How do I do that?

---

### Post by almaghi on 2011-02-14
> **PJOS13 said:**
> Hi, I'm trying to remove KDE, and I found in another thread that th method described here is the best: [http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

But when I run that in the terminal I get this error: 

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not going to be installed
E: Broken packages

```

any suggestions?

[http://wwww.ubuntuforums.org/showthread.php?p=10119795](http://wwww.ubuntuforums.org/showthread.php?p=10119795)

> **koolcracker said:**
> I found that the package 'libgif4' was the one causing problems, so I removed that from the long command and everything seemed to uninstall just fine.

The new command turned out to be:
```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark bluedevil cdparanoia cdrdao docbook-xsl docbook-xsl-doc-html dolphin dragonplayer gdebi-core gdebi-kde gnupg-agent gnupg2 gtk2-engines-qtcurve gwenview hal hal-info ibus-qt4 icoutils jockey-kde k3b k3b-data kaddressbook kamera kate kcalc kde-config-gtk kde-config-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-libs-data kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-kio-plugins kdesudo kdm kdoctools kfind khelpcenter4 kinfocenter klipper kmag kmail kmix kmousetool knm-runtime knotes konsole kontact kopete kopete-message-indicator korganizer kpackagekit kppp krdc krfb krosspython ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-netbook-default-settings kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadiprivate1 libao-common libao4 libattica0 libaudio2 libbluedevil1 libboost-program-options1.42.0 libcln6 libclucene0ldbl libdbusmenu-qt2 libdebconf-kde0 libdirectfb-1.2-9 libepub0 libflac++6 libgpgme++2 libgps19 libhal-storage1 libhal1 libibus-qt1 libilmbase6 libindicate-qt0 libiodbc2 libk3b6 libkabc4 libkatepartinterfaces4 libkblog4 libkcal4 libkcddb4 libkdcraw8 libkde3support4 libkdecorations4 libkdecore5 libkdepim4 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkephal4 libkexiv2-8 libkfile4 libkholidays4 libkhtml5 libkimap4 libkimproxy4 libkio5 libkipi7 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq5 libkonq5-templates libkontactinterface4 libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkpty4 libkresources4 libkrosscore4 libkrossui4 libksba8 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libktexteditor4 libktnef4 libktorrent-l10n libktorrent2 libkunitconversion4 libkutils4 libkwineffects1a libkworkspace4 libkxmlrpcclient4 liblastfm0 libloudmouth1-0 libmailtransport4 libmessagecore4 libmessagelist4 libmicroblog4 libmimelib4 libmng1 libmodplug1 libmpcdec6 libmsn0.3 libmysqlclient16 libnepomuk4 libnepomukquery4a libokularcore1 libopenexr6 libotr2 libpackagekit-glib2-14 libpackagekit-qt-14 libphonon4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4b libplasmagenericshell4 libpolkit-qt-1-0 libpoppler-qt4-3 libprocesscore4a libprocessui4a libqalculate5 libqapt-runtime libqapt1 libqca2 libqca2-plugin-ossl libqgpgme1 libqimageblitz4 libqjson0 libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libqtwebkit4 libreadline5 libsolid4 libsolidcontrol4a libsolidcontrolifaces4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libsyndication4 libtag-extras1 libtaskmanager4a libtelepathy-qt4-0 libthreadweaver4 libts-0.0-0 libvirtodbc0 libvncserver0 libweather-ion4a libxcb-shape0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-client-core-5.1 mysql-common mysql-server-core-5.1 network-manager-pptp-kde odbcinst odbcinst1debian2 okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete packagekit packagekit-backend-aptcc phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback plasma-widget-menubar plasma-widget-message-indicator plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text polkit-kde-1 printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip qapt-batch quassel quassel-data rekonq shared-desktop-ontologies smartdimmer software-properties-kde soprano-daemon system-config-printer-kde systemsettings tsconf ttf-dejavu ttf-dejavu-extra update-manager-kde usb-creator-kde userconfig virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common && sudo apt-get install ubuntu-desktop
```

---

