---
title: "how to make kubuntu a better distro"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by nerdy_kid on 2010-05-31
Ive heard that Kubuntu is a bug ridden distro (compared to other KDE4 implementations), and i belive it, but i dont want to switch.  Would removing kubuntu-default-settings give me basically a vanilla kde install?  Thus solving the bugginess?

---

### Post by ankspo71 on 2010-06-01
Hi,
Have you tried the latest release of Kubuntu yet? I feel it has very few kde related bugs. It's faster than previous 4.xx versions too. I highly recommend trying out the Kubuntu 10.04 live cd to see how everything works for you first, before you actually attempt to install it.

I have been hearing people say that the wireless part of the network manager in KDE is buggy, but anyone can also use gnome's network manager or even wicd too. The KDE network manager is working pretty good for me, however I think it could be a little better at reconnecting wireless though. 

Kubuntu comes with KDE 4.4.2, but I'm using KDE 4.4.3 from a PPA for Kubuntu, only because I was curious. I'll give you the details in case you aren't satisfied with 4.4.2.

Easiest instructions to upgrade to KDE 4.4.3 using the PPA:
```
sudo add-apt-repository ppa:kubuntu-ppa/ppa
sudo apt-get update
sudo apt-get upgrade
```

Kubuntu PPA homepage:
[https://launchpad.net/~kubuntu-ppa/+archive/ppa](https://launchpad.net/~kubuntu-ppa/+archive/ppa) 

If you feel that Kubuntu should be faster, the 3D effects animation speed can be changed, and it makes a world of difference for me. 

I'm a bigger fan of the ext3 file system rather than the ext4 file system right now. For me it seems a little quicker all around (more noticeable in Kubuntu than Ubuntu), but it is much faster at installing packages and updates (dpkg) in both Ubuntu and Kubuntu.

---

### Post by ankspo71 on 2010-06-01
Ahh, I misunderstood your question...

There is a package called kde-full, which is supposed to be the original KDE Desktop. I'm not sure if it would be easy to get rid of the Kubuntu kde packages though. 

Alright I found something. You can use a modified command from here:
[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

Below will try to remove all Kubuntu related packages and install kde-full. It's a modified command from the above link. Make backups first before trying this.
```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint freespacenotifier gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 icoutils ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kbluetooth kcalc kcm-gtk kcm-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knm-runtime knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete kopete-message-indicator korganizer kpackagekit kppp krdc krfb krosspython ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libattica0 libaudio2 libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2 libepub0 libexiv2-6 libflac++6 libibus-qt1 libindicate-qt0 libiodbc2 libk3b6 libkcddb4 libkdcraw8 libkdecorations4 libkdepim4 libkephal4 libkexiv2-8 libkfontinst4 libkipi7 libkleo4 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkopete4 libkpgp4 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libkwineffects1 libkworkspace4 liblastfm0 libmimelib4 libmng1 libmodplug0c2 libmpcdec3 libmsn0.3 libmysqlclient16 libokularcore1 libotr2 libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4 libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4 libplasmagenericshell4 libpolkit-qt-1-0 libpoppler-qt4-3 libprocesscore4 libprocessui4 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libtag-extras1 libtaskmanager4 libvncserver0 libweather-ion4 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-client-core-5.1 mysql-common mysql-server-core-5.1 network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback plasma-widget-message-indicator plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo polkit-kde-1 printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip quassel quassel-data shared-desktop-ontologies software-properties-kde soprano-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde usb-creator-kde userconfig virtuoso-nepomuk && sudo apt-get install kde-full
```
Hope this helps.

---

### Post by nerdy_kid on 2010-06-02
> **ankspo71 said:**
> Ahh, I misunderstood your question...

There is a package called kde-full, which is supposed to be the original KDE Desktop. I'm not sure if it would be easy to get rid of the Kubuntu kde packages though. 

Alright I found something. You can use a modified command from here:
[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

Below will try to remove all Kubuntu related packages and install kde-full. It's a modified command from the above link. Make backups first before trying this.
```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint freespacenotifier gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 icoutils ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kbluetooth kcalc kcm-gtk kcm-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knm-runtime knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete kopete-message-indicator korganizer kpackagekit kppp krdc krfb krosspython ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libattica0 libaudio2 libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2 libepub0 libexiv2-6 libflac++6 libibus-qt1 libindicate-qt0 libiodbc2 libk3b6 libkcddb4 libkdcraw8 libkdecorations4 libkdepim4 libkephal4 libkexiv2-8 libkfontinst4 libkipi7 libkleo4 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkopete4 libkpgp4 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libkwineffects1 libkworkspace4 liblastfm0 libmimelib4 libmng1 libmodplug0c2 libmpcdec3 libmsn0.3 libmysqlclient16 libokularcore1 libotr2 libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4 libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4 libplasmagenericshell4 libpolkit-qt-1-0 libpoppler-qt4-3 libprocesscore4 libprocessui4 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libtag-extras1 libtaskmanager4 libvncserver0 libweather-ion4 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-client-core-5.1 mysql-common mysql-server-core-5.1 network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback plasma-widget-message-indicator plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo polkit-kde-1 printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip quassel quassel-data shared-desktop-ontologies software-properties-kde soprano-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde usb-creator-kde userconfig virtuoso-nepomuk && sudo apt-get install kde-full
```
Hope this helps.

thanks a bunch :) will try!

---

### Post by ankspo71 on 2010-06-02
Hi,
What type of bugs were you having? Have you tried asking about them here or over at the Kubuntu forums? ([http://www.kubuntuforums.net/](http://www.kubuntuforums.net/))

Replacing the default kubuntu-desktop packages with the kde-full packages doesn't look like it will make that big of a difference, it will be different though. Kubuntu added things things like some artwork, shortcuts, and decided which applications should be included etc. The Kubuntu developers compiled all of the same packages that are in kde-full too as far as I know. You might be better off trying the upgrade first, then if you still have bugs you can remove the PPA from your sources.list, then try the kde-full package.

---

### Post by wojox on 2010-06-02
Try openSUSUE 11.2 KDE It rocks.

---

### Post by nerdy_kid on 2010-06-08
> **ankspo71 said:**
> Hi,
What type of bugs were you having? Have you tried asking about them here or over at the Kubuntu forums? ([http://www.kubuntuforums.net/](http://www.kubuntuforums.net/))

Replacing the default kubuntu-desktop packages with the kde-full packages doesn't look like it will make that big of a difference, it will be different though. Kubuntu added things things like some artwork, shortcuts, and decided which applications should be included etc. The Kubuntu developers compiled all of the same packages that are in kde-full too as far as I know. You might be better off trying the upgrade first, then if you still have bugs you can remove the PPA from your sources.list, then try the kde-full package.


sorry for the slow response guys, i havnt been on the forums for a while.

Well the buggyness i was experancing was a slow right click menu in the file managers (konquerer, dolphin).  Through proccess of elimination (i.e. wiping ubuntu install and install the commandline system from the alternate cd) i have discovered that ark was causing it.  I havnt reported my findings on the bug trackers.  

removing the kubuntu-default-settings did solve a lot of de problems though (like panels that wouldnt resize correctly etc)

i tried opensuse and it is sooooooooo sllooooowww

---

