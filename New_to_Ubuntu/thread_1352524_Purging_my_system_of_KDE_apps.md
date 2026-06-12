---
title: "Purging my system of KDE apps"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-12-11
Shortly after I installed ubuntu over a year or so ago, I saw loads of nice free software on offer from Synaptic and installed loads of stuff on the assumption that I might one day want to use them. I didn't understand the difference between KDE and Gnome at that time.

Anyway, what I'd like to do now is to clear out some apps that I don't use. As KDE apps look quite ugly on a Gnome DE, I tend not to use them.

I've been looking around for just one package, or perhaps just a few packages, that I need to remove that is a dependency of all KDE apps.

I thought that kdebase ought to be a good contender, but that's not installed.

What are installed that seems to have lots of dependent packages are kdelibs4c2a and kdebase-runtime, but is there a better candidate?

---

### Post by leef on 2009-12-11
qt is to kde what gtk is to gnome, I suggest that you try to uninstall qt (QT3 and QT4) and all apps that depend on it which would un-install all kde apps however not exactly sure how you would do that, sorry mate.

---

### Post by Captain_tux on 2009-12-11
> **leef said:**
> qt is to kde what gtk is to gnome, I suggest that you try to uninstall qt (QT3 and QT4) and all apps that depend on it which would un-install all kde apps however not exactly sure how you would do that, sorry mate.

sudo apt-get remove name_of_app_here ?

---

### Post by SuperSonic4 on 2009-12-11
> **Captain_tux said:**
> sudo apt-get remove name_of_app_here ?

Would take far too long

I would suggest ```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kcm-gtk kde-icons-oxygen kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4 kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 kipi-plugins klipper kmag kmail kmix kmousetool knotes konq-plugins konq-plugins-l10n konqueror konqueror-nsplugins konqueror-plugin-searchbar konqueror-plugins konsole kontact kopete korganizer kpackagekit kppp krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin-style-qtcurve language-selector-qt libakonadiprivate1 libao2 libaudio2 libboost-program-options1.38.0 libclucene0ldbl libepub0 libexiv2-5 libfftw3-3 libflac++6 libindicate-qt0 libjpeg-progs libk3b6 libkabcommon4 libkcddb4 libkdcraw7 libkdecorations4 libkdepim4 libkexiv2-7 libkipi6 libkleo4 libknotificationitem1 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkontactinterfaces4 libkopete4 libkorundum4-ruby1.8 libkpgp4 libksane0 libksieve4 libkwineffects1 liblancelot0 liblastfm0 liblzma0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libokularcore1 libotr2 libpackagekit-glib11 libpackagekit-qt11 libplasma3 libpolkit-dbus2 libpolkit-grant2 libpolkit-qt0 libpolkit2 libpoppler-qt4-3 libqca2 libqca2-plugin-ossl libqimageblitz4 libqscintilla2-5 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-ruby1.8 libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libruby1.8 libscim8c2a libsmokekde4-2 libsmokeqt4-2 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libtag-extras1 libtidy-0.99-0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-server-core-5.1 okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme packagekit packagekit-backend-apt phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-googlecalendar plasma-widget-indicatordisplay plasma-widget-kimpanel plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace policykit printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip4 quassel quassel-data ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch system-config-printer-kde systemsettings ttf-arphic-uming ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde usb-creator-kde userconfig
```


Source: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Might not get rid of all of them but probably most

---

### Post by leef on 2009-12-11
> **Captain_tux said:**
> sudo apt-get remove name_of_app_here ?

yeah but I'm not sure if that removes the packages that depend on it, also I'm not sure if ubuntu has qt as a dummy package for qt or if you have to enter the version number, etc :D. I'm more used to gentoo :(.

---

### Post by Roger Allott on 2009-12-12
> **SuperSonic4 said:**
> 
I would suggest ```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kcm-gtk kde-icons-oxygen kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4 kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 kipi-plugins klipper kmag kmail kmix kmousetool knotes konq-plugins konq-plugins-l10n konqueror konqueror-nsplugins konqueror-plugin-searchbar konqueror-plugins konsole kontact kopete korganizer kpackagekit kppp krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin-style-qtcurve language-selector-qt libakonadiprivate1 libao2 libaudio2 libboost-program-options1.38.0 libclucene0ldbl libepub0 libexiv2-5 libfftw3-3 libflac++6 libindicate-qt0 libjpeg-progs libk3b6 libkabcommon4 libkcddb4 libkdcraw7 libkdecorations4 libkdepim4 libkexiv2-7 libkipi6 libkleo4 libknotificationitem1 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkontactinterfaces4 libkopete4 libkorundum4-ruby1.8 libkpgp4 libksane0 libksieve4 libkwineffects1 liblancelot0 liblastfm0 liblzma0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libokularcore1 libotr2 libpackagekit-glib11 libpackagekit-qt11 libplasma3 libpolkit-dbus2 libpolkit-grant2 libpolkit-qt0 libpolkit2 libpoppler-qt4-3 libqca2 libqca2-plugin-ossl libqimageblitz4 libqscintilla2-5 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-ruby1.8 libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libruby1.8 libscim8c2a libsmokekde4-2 libsmokeqt4-2 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libtag-extras1 libtidy-0.99-0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-server-core-5.1 okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme packagekit packagekit-backend-apt phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-googlecalendar plasma-widget-indicatordisplay plasma-widget-kimpanel plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace policykit printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip4 quassel quassel-data ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch system-config-printer-kde systemsettings ttf-arphic-uming ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde usb-creator-kde userconfig
```


Source: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Might not get rid of all of them but probably most

Thanks for that - particularly the very helpful link.

It seems to get rid of a heck of a lot, including stuff that I'm amazed to find are considered KDE apps. For example, these were all removed:
[LIST][*]avidemux (the GTK version!)
[*]gimp-plugin-registry
[*]gimp-ufraw
[*]gnome-art
[*]gnome-volume-manager
[*]gnome-mount
[*]gnome-splashscreen-manager
[*]nautilus-image-converter
[*]opera
[*]mysql-navigator[/LIST]

---

### Post by earthpigg on 2009-12-12
> **Roger Allott said:**
> 
It seems to get rid of a heck of a lot, including stuff that I'm amazed to find are considered KDE apps. For example, these were all removed:
[LIST][*]avidemux (the GTK version!)
[*]gimp-plugin-registry
[*]gimp-ufraw
[*]gnome-art
[*]gnome-volume-manager
[*]gnome-mount
[*]gnome-splashscreen-manager
[*]nautilus-image-converter
[*]opera
[*]mysql-navigator[/LIST]

then do not run that command. my guess would be it hasnt been updated since 9.10 came out... or there is just a typo. either way, removing gnome-mount is clearly not what you had in mind.

search for 'qt' in synaptic, and sort by installed. pick a qt related package at random and click to remove it, but don't hit apply just yet. read carefully - synaptic will tell you what 'depends' on the qt-related package you selected. the list will be several items long. read it.

your mystery package will be in that list. if not, try a few different qt related packages. it will be listed as a depend somewhere.

and, if not... just go ahead and remove everything qt-related. you can always reinstall later, after all. nothing system critical relies on qt.

---

### Post by Roger Allott on 2009-12-12
> **earthpigg said:**
> then do not run that command. my guess would be it hasnt been updated since 9.10 came out... or there is just a typo. either way, removing gnome-mount is clearly not what you had in mind.



The problem is though that it only tells you that it's removing those packages while the command is running!

I've looked up gnome-volume-manager, which has gnome-mount as a dependency, and found that it requires HAL, which has been deprecated in karmic I think.

Which makes me wonder whether I shouldn't reinstall gnome-volume-manager because there's some new package that replaces it. But what?

---

### Post by Roger Allott on 2009-12-12
Before I reboot, I'd appreciate it if someone would have a quick look through the list of packages that were removed when I ran that command and let me know whether any of them are system essentials (like gnome-mount, for example) that should be reinstalled.

```
The following packages will be REMOVED
  adept amarok amarok-common amarok-utils ams anymeal ardour
  audacious-plugins-extra audacity avidemux avidemux-plugins blender cdrdao
  creox denemo dssi-example-plugins dvdrip earth3d exiv2 ffado-mixer-qt4
  flightgear flvtool2 fontmatrix freqtweak gcdmaster gem genpo
  gimp-plugin-registry gimp-ufraw gnome-art gnome-mount
  gnome-splashscreen-manager gnome-volume-manager grass
  gstreamer0.10-plugins-bad gxine hplip-gui hugin hugin-tools hydrogen
  imagemagick jackeq jamin kde-icons-oxygen kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data
  kdemultimedia-kio-plugins kdepimlibs-data kdepimlibs5 khelpcenter4
  libakonadiprivate1 libao2 libaqbanking29-plugins-qt libart2-ruby1.8
  libatk1-ruby1.8 libaubio2 libaudio-dev libaudio2 libavahi-qt3-1
  libboost-program-options1.38.0 libcairo-ruby1.8 libclucene0ldbl libexiv2-5
  libfftw3-3 libflac++6 libgconf2-ruby libgconf2-ruby1.8
  libgdk-pixbuf2-ruby1.8 libglade2-ruby libglade2-ruby1.8 libglib2-ruby1.8
  libgnome2-ruby libgnome2-ruby1.8 libgnomecanvas2-ruby1.8 libgtk2-ruby1.8
  libjpeg-progs libkcddb4 libknotificationitem1 libkonq5 libkonq5-templates
  liblastfm0 liblzma0 libmodplug0c2 libmpcdec3 libofa0 libopenscenegraph56
  libotr2 libpango1-ruby1.8 libphonon4 libplasma3 libpolkit-dbus2
  libpolkit-gnome0 libpolkit-grant2 libpolkit-qt0 libpolkit2 libprojectm2
  libqbanking8 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core
  libqt4-dbus libqt4-designer libqt4-dev libqt4-gui libqt4-help libqt4-network
  libqt4-opengl libqt4-opengl-dev libqt4-phonon libqt4-qt3support
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui
  libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml
  libruby1.8 libscim8c2a libsoprano4 libstreamanalyzer0 libstreams0 libsynfig0
  libsynfigapp0 libtag-extras1 libtidy-0.99-0 libtunepimp5 libtunepimp5-mp3
  libvips15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin
  libxine1-console libxine1-ffmpeg libxine1-gnome libxine1-misc-plugins
  libxine1-x libzip1 lmms lmms-vst mencoder mixxx mozilla-mplayer mpg321
  mplayer mplayer-fonts mplayer-nogui mscore muse mysql-navigator
  nautilus-image-converter odt2txt openoffice.org opera phonon
  phonon-backend-gstreamer phonon-backend-xine pidgin-otr pokerth policykit
  policykit-gnome python-kde4 python-qt4 python-qt4-dbus python-sip4
  python-tunepimp python-utidylib qamix qcad qcad-doc qjackctl qsynth
  qt3-assistant qt4-designer qt4-dev-tools qt4-qtconfig qtstalker ruby ruby1.8
  scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule
  scim-modules-socket scim-modules-table scim-tables-additional scim-tables-zh
  scribus soprano-daemon speedcrunch stopmotion swh-plugins synfigstudio
  system-config-printer-kde terminatorx timidity timidity-daemon
  ttf-arphic-uming ttf-dejavu ttf-dejavu-extra umbrello vlc vlc-nox
  vlc-plugin-pulse vorbis-tools wine xine-ui xjadeo zynaddsubfx
```

---

### Post by mkvnmtr on 2009-12-12
Just yesterday I uninstalled a lot of kde packages that had beeniinstalled when my son installed a bunch of games to see if he liked them. I just typed kde in the search box of the package manager. Then it took about 3 minutes to delete them through the package manager-

---

### Post by slakkie on 2009-12-12
```

rm-metapkg () {
        local i
        for i in "$@"
        do
                sudo aptitude markauto $(apt-cache depends $i | egrep -v "Conflict|Replaces" | sed -e 's/[<>]//g' | tail -n +2| awk '{print $NF}')
        done
}

```

then run rm-metapkg kubuntu-desktop

And you might also want to run after that:
```

sudo aptitude remove $(dpkg -l | grep kde | awk '{print $2}')

```

That is how I removed Gnome from my system.

---

