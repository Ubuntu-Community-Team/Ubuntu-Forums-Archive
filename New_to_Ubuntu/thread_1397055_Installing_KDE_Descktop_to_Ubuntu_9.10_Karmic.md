---
title: "Installing KDE Descktop to Ubuntu 9.10 Karmic"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by zfranciscus on 2010-02-02
Hi,

I want to have KDE look and feel in for my desktop. So I decided to install Kubuntu Desktop from Synaptic Package Manager. To my surprise it downloaded every Kubuntu desktop application like Amarok, Kope, etc. 

Does any one know how to install KDE Desktop in Ubuntu without having to get kubuntu desktop applications such as Amarok, Kope, etc. 

Thank you

---

### Post by tom.swartz07 on 2010-02-02
> **zfranciscus said:**
> Hi,

I want to have KDE look and feel in for my desktop. So I decided to install Kubuntu Desktop from Synaptic Package Manager. To my surprise it downloaded every Kubuntu desktop application like Amarok, Kope, etc. 

Does any one know how to install KDE Desktop in Ubuntu without having to get kubuntu desktop applications such as Amarok, Kope, etc. 

Thank you

Unfortunately, thats the one drawback to having the 2 desktop managers. You need the applications "front ends" so that they run properly in graphical windows within the respective desktop environments.

If you want to go 'Pure' kubuntu or ubuntu, you could follow the guides here.

Pure KDE:
```
sudo apt-get remove aisleriot alacarte app-install-data-partner apport-gtk aptdaemon at-spi binfmt-support brasero brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktop-file-utils desktopcouch devicekit-power dmz-cursor-theme doc-base docbook-xml empathy empathy-doc eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-documentation-en evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot file-roller firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support gamin gcalctool gconf-defaults-service gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu glchess glines gnect gnibbles gnobots2 gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-blackjack gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games gnome-games-common gnome-icon-theme gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gnometris gnomine gnotravex gnotski gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtali gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-theme humanity-icon-theme iagno ibus ibus-gtk ibus-m17n ibus-table indicator-applet indicator-applet-session indicator-messages indicator-session jockey-gtk language-selector launchpad-integration libanthy0 libart-2.0-2 libart2.0-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-1 libcroco3 libcryptui0 libcurl3 libdbusmenu-glib0 libdbusmenu-gtk0 libdecoration0 libdevkit-power-gobject1 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30 libesd-alsa0 libespeak1 libevdocument1 libevent-1.4-2 libevview1 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.0-cil libgcr0 libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata5 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgdu0 libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime-2.4-2 libgmime2.2a-cil libgnome-bluetooth7 libgnome-desktop-2-11 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgsf-1-114 libgsf-1-common libgssdp-1.0-1 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-2 libgupnp-igd-1.0-2 libgvfscommon0 libgweather-common libgweather1 libibus1 libidl0 libiec61883-0 libindicate-gtk1 libjson-glib-1.0-0 libkpathsea4 liblaunchpad-integration1 liblircclient0 liblouis-data liblouis0 liblpint-bonobo0 libm17n-0 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 liboil0.3 liboobs-1-4 liborbit2 libotf0 libpam-gnome-keyring libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-agent-1-0 libpolkit-gtk-1-0 libpoppler-glib4 libportaudio2 libprotobuf3 libproxy0 libpst4 libpulse-browse0 libpulse-mainloop-glib0 libpurple-bin libpurple0 librarian0 libraw1394-11 librsvg2-2 librsvg2-common libsctp1 libsexy2 libshout3 libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libtie-ixhash-perl libtotem-plparser12 libtrackerclient0 libunique-1.0-0 libuuid-perl libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 lksctp-tools m17n-contrib m17n-db media-player-info mesa-utils metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon notify-osd notify-osd-icons obexd-client onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pkg-config policykit-1-gnome protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon-gtk python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-fstab python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-ibus python-launchpad-integration python-libxml2 python-louis python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pyinotify python-pyorbit python-rdflib python-rsvg python-serial python-sexy python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit rarian-compat rhythmbox same-gnome screen-resolution-extra screensaver-default-images seahorse sgml-data software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntu-xsplash-artwork ubuntuone-client ubuntuone-client-gnome update-manager update-notifier usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xsplash xulrunner-1.9.1 xulrunner-1.9.1-gnome-support yelp zenity && sudo apt-get install kubuntu-desktop

```

Pure Ubuntu:
```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kcm-gtk kde-icons-oxygen kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4 kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 kipi-plugins klipper kmag kmail kmix kmousetool knotes konq-plugins konq-plugins-l10n konqueror konqueror-nsplugins konqueror-plugin-searchbar konqueror-plugins konsole kontact kopete korganizer kpackagekit kppp krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin-style-qtcurve language-selector-qt libakonadiprivate1 libao2 libaudio2 libboost-program-options1.38.0 libclucene0ldbl libepub0 libexiv2-5 libfftw3-3 libflac++6 libindicate-qt0 libjpeg-progs libk3b6 libkabcommon4 libkcddb4 libkdcraw7 libkdecorations4 libkdepim4 libkexiv2-7 libkipi6 libkleo4 libknotificationitem1 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkontactinterfaces4 libkopete4 libkorundum4-ruby1.8 libkpgp4 libksane0 libksieve4 libkwineffects1 liblancelot0 liblastfm0 liblzma0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libokularcore1 libotr2 libpackagekit-glib11 libpackagekit-qt11 libplasma3 libpolkit-dbus2 libpolkit-grant2 libpolkit-qt0 libpolkit2 libpoppler-qt4-3 libqca2 libqca2-plugin-ossl libqimageblitz4 libqscintilla2-5 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-ruby1.8 libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libruby1.8 libscim8c2a libsmokekde4-2 libsmokeqt4-2 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libtag-extras1 libtidy-0.99-0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-server-core-5.1 okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme packagekit packagekit-backend-apt phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-googlecalendar plasma-widget-indicatordisplay plasma-widget-kimpanel plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace policykit printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip4 quassel quassel-data ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch system-config-printer-kde systemsettings ttf-arphic-uming ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde usb-creator-kde userconfig && sudo apt-get install ubuntu-desktop

```

---

### Post by running_rabbit07 on 2010-02-02
[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

---

### Post by sandyd on 2010-02-02
if your using karmic, install kde-minimal

---

### Post by *Raz0r* on 2010-02-02
Even if you install the minimum version, there will be still a lot of other unneeded applications along with it. I guess they are just a part of KDE

---

### Post by lovinglinux on 2010-02-02
> ***Raz0r* said:**
> Even if you install the minimum version, there will be still a lot of other unneeded applications along with it. I guess they are just a part of KDE

kde-minimal is great and does not clutter your desktop.

I would also recommend installing kdeplasma-addons.

If you want to launch kde interface without logging out from gnome, then open the "Run" tool (F12 I guess) and type **plasma-desktop**.

---

### Post by samantha_ on 2010-02-02
> **lovinglinux said:**
> kde-minimal is great and does not clutter your desktop.

I would also recommend installing kdeplasma-addons.

If you want to launch kde interface without logging out from gnome, then open the "Run" tool (F12 I guess) and type **plasma**.

isnt it plasma-desktop, not plasma?

---

### Post by lovinglinux on 2010-02-02
> **samantha_ said:**
> isnt it plasma-desktop, not plasma?

:oops: yep, it is. Sorry for that. I have been running KDE only for so long now, that I forgot the correct command :)

---

### Post by vikjon0 on 2010-03-20
> if your using karmic, install kde-minimal
__________________

Thanks! I was looking for that.
But this includes kdm, is there no package that gives a bare desktop only?

EDIT2:
--no-install-recommends kde-minimal works fine.

Otherwise kdebase-workspace-bin is even more minimal.

---

### Post by kio_http on 2010-03-21
If you chose to install Kubuntu-desktop.

run ```
aptitude install kubuntu-desktop
```

It will make KDE much more easier to remove in future.

Having all Kubuntu and Ubuntu apps installed is a problem as GNOME's menu becomes full. However KDE is manageable as its menu uses a search and scroll bars. The similar idea that Windows Vista/7 use except that KDE had it ages before Microsoft Windows.

---

### Post by vikjon0 on 2010-03-21
> It will make KDE much more easier to remove in future.

Having all Kubuntu and Ubuntu apps installed is a problem as GNOME's menu becomes full. However KDE is manageable as its menu uses a search and scroll bars. The similar idea that Windows Vista/7 use except that KDE had it ages before Microsoft Windows.

Well, the whole point was NOT to do that. It is not only about the menus, besides as you say the gnome menus will be screwed up so will all other menus except possibly KDE's.

---

### Post by Tikkyca on 2010-03-21
When i search KDE or Kubuntu in synaptic i install kubuntu-desktop,and everything works great,some apps come with that installed also,and i usually uninstall some programs that i don't need from that.

---

