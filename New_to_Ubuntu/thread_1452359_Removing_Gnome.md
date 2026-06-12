---
title: "Removing Gnome"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by themarker0 on 2010-04-11
So i got LXDE working via synaptic manager, and i want to remove gnome, it runs slow, and i have no need for it. Whats the correct way removing it? I want the programs to stay. Would it be better just to used LXDE default, and leave gnome on? Space isn't issue. Speed is though..


Tm0.

---

### Post by tom.swartz07 on 2010-04-11
> **themarker0 said:**
> So i got LXDE working via synaptic manager, and i want to remove gnome, it runs slow, and i have no need for it. Whats the correct way removing it? I want the programs to stay. Would it be better just to used LXDE default, and leave gnome on? Space isn't issue. Speed is though..


Tm0.

You just need to copy this monster of a command into your terminal:
```
sudo apt-get remove aisleriot alacarte app-install-data-partner apport-gtk aptdaemon at-spi binfmt-support brasero brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktop-file-utils desktopcouch devicekit-power dmz-cursor-theme doc-base docbook-xml empathy empathy-doc eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-documentation-en evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot file-roller firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support gamin gcalctool gconf-defaults-service gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu glchess glines gnect gnibbles gnobots2 gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-blackjack gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games gnome-games-common gnome-icon-theme gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gnometris gnomine gnotravex gnotski gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtali gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-theme humanity-icon-theme iagno ibus ibus-gtk ibus-m17n ibus-table indicator-applet indicator-applet-session indicator-messages indicator-session jockey-gtk language-selector launchpad-integration libanthy0 libart-2.0-2 libart2.0-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-1 libcroco3 libcryptui0 libcurl3 libdbusmenu-glib0 libdbusmenu-gtk0 libdecoration0 libdevkit-power-gobject1 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30 libesd-alsa0 libespeak1 libevdocument1 libevent-1.4-2 libevview1 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.0-cil libgcr0 libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata5 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgdu0 libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime-2.4-2 libgmime2.2a-cil libgnome-bluetooth7 libgnome-desktop-2-11 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgsf-1-114 libgsf-1-common libgssdp-1.0-1 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-2 libgupnp-igd-1.0-2 libgvfscommon0 libgweather-common libgweather1 libibus1 libidl0 libiec61883-0 libindicate-gtk1 libjson-glib-1.0-0 libkpathsea4 liblaunchpad-integration1 liblircclient0 liblouis-data liblouis0 liblpint-bonobo0 libm17n-0 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 liboil0.3 liboobs-1-4 liborbit2 libotf0 libpam-gnome-keyring libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-agent-1-0 libpolkit-gtk-1-0 libpoppler-glib4 libportaudio2 libprotobuf3 libproxy0 libpst4 libpulse-browse0 libpulse-mainloop-glib0 libpurple-bin libpurple0 librarian0 libraw1394-11 librsvg2-2 librsvg2-common libsctp1 libsexy2 libshout3 libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libtie-ixhash-perl libtotem-plparser12 libtrackerclient0 libunique-1.0-0 libuuid-perl libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 lksctp-tools m17n-contrib m17n-db media-player-info mesa-utils metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon notify-osd notify-osd-icons obexd-client onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pkg-config policykit-1-gnome protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon-gtk python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-fstab python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-ibus python-launchpad-integration python-libxml2 python-louis python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pyinotify python-pyorbit python-rdflib python-rsvg python-serial python-sexy python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit rarian-compat rhythmbox same-gnome screen-resolution-extra screensaver-default-images seahorse sgml-data software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntu-xsplash-artwork ubuntuone-client ubuntuone-client-gnome update-manager update-notifier usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xsplash xulrunner-1.9.1 xulrunner-1.9.1-gnome-support yelp zenity
```

Thats all you need to do! All this does is removes every part of the Ubuntu Desktop package. As long as you have LXDE installed great, you'll be all set after that, It will automatically boot to your Lubuntu desktop.

---

### Post by themarker0 on 2010-04-11
> **tom.swartz07 said:**
> You just need to copy this monster of a command into your terminal:
```
sudo apt-get remove aisleriot alacarte app-install-data-partner apport-gtk aptdaemon at-spi binfmt-support brasero brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktop-file-utils desktopcouch devicekit-power dmz-cursor-theme doc-base docbook-xml empathy empathy-doc eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-documentation-en evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot file-roller firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support gamin gcalctool gconf-defaults-service gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu glchess glines gnect gnibbles gnobots2 gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-blackjack gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games gnome-games-common gnome-icon-theme gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gnometris gnomine gnotravex gnotski gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtali gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-theme humanity-icon-theme iagno ibus ibus-gtk ibus-m17n ibus-table indicator-applet indicator-applet-session indicator-messages indicator-session jockey-gtk language-selector launchpad-integration libanthy0 libart-2.0-2 libart2.0-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-1 libcroco3 libcryptui0 libcurl3 libdbusmenu-glib0 libdbusmenu-gtk0 libdecoration0 libdevkit-power-gobject1 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30 libesd-alsa0 libespeak1 libevdocument1 libevent-1.4-2 libevview1 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.0-cil libgcr0 libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata5 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgdu0 libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime-2.4-2 libgmime2.2a-cil libgnome-bluetooth7 libgnome-desktop-2-11 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgsf-1-114 libgsf-1-common libgssdp-1.0-1 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-2 libgupnp-igd-1.0-2 libgvfscommon0 libgweather-common libgweather1 libibus1 libidl0 libiec61883-0 libindicate-gtk1 libjson-glib-1.0-0 libkpathsea4 liblaunchpad-integration1 liblircclient0 liblouis-data liblouis0 liblpint-bonobo0 libm17n-0 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 liboil0.3 liboobs-1-4 liborbit2 libotf0 libpam-gnome-keyring libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-agent-1-0 libpolkit-gtk-1-0 libpoppler-glib4 libportaudio2 libprotobuf3 libproxy0 libpst4 libpulse-browse0 libpulse-mainloop-glib0 libpurple-bin libpurple0 librarian0 libraw1394-11 librsvg2-2 librsvg2-common libsctp1 libsexy2 libshout3 libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libtie-ixhash-perl libtotem-plparser12 libtrackerclient0 libunique-1.0-0 libuuid-perl libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 lksctp-tools m17n-contrib m17n-db media-player-info mesa-utils metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon notify-osd notify-osd-icons obexd-client onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pkg-config policykit-1-gnome protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon-gtk python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-fstab python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-ibus python-launchpad-integration python-libxml2 python-louis python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pyinotify python-pyorbit python-rdflib python-rsvg python-serial python-sexy python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit rarian-compat rhythmbox same-gnome screen-resolution-extra screensaver-default-images seahorse sgml-data software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntu-xsplash-artwork ubuntuone-client ubuntuone-client-gnome update-manager update-notifier usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xsplash xulrunner-1.9.1 xulrunner-1.9.1-gnome-support yelp zenity
```Thats all you need to do! All this does is removes every part of the Ubuntu Desktop package. As long as you have LXDE installed great, you'll be all set after that, It will automatically boot to your Lubuntu desktop.

Holy crap. Is gnome needed for some programs i want though? Gedit, jokosher, audacity, gimp etc.

---

### Post by egalvan on 2010-04-11
> **themarker0 said:**
> So i got LXDE working via synaptic manager, and i want to remove gnome, it runs slow, and i have no need for it. Whats the correct way removing it? **I want the programs to stay. **Would it be better just to used LXDE default, and leave gnome on? Space isn't issue. **Speed is though.**.
Tm0.

What programs are you talking about here?
Gnome-based ones?

As for speed...
Once you boot into LXDE, Gnome is not used, unless you run a program that requires a library or other Gnome-centric part.
Then only those parts needed will be loaded.


The best way to hve only LXDE is to do a CLI install (also called a Server Install)
and add the LXDE desktop.
This will not **install** anything you don´t want (no GnomeKDE pieces)...
if you then try to install some program that uses Gnome or KDE pieces, at least the installer will let you know, and you can then make an informed decision.

---

### Post by themarker0 on 2010-04-11
> **egalvan said:**
> What programs are you talking about here?
Gnome-based ones?

As for speed...
Once you boot into LXDE, Gnome is not used, unless you run a program that requires a library or other Gnome-centric part.
Then only those parts needed will be loaded.


The best way to hve only LXDE is to do a CLI install (also called a Server Install)
and add the LXDE desktop.
This will not load anything you don´t want (no GnomeKDE pieces)...
if you then try to install some program that uses Gnome or KDE pieces, at least the installer will let you know, and you can then make an informed decision.

Well i listed my programs, and it seems they are needed. If the processes are killed after the program closes i have no real issue. :)

---

### Post by Otis Spunkmiyer on 2010-04-11
Is there a difference in loading LXDE from Alt-F2 update as oppose to what's in Synaptic ?
I did Synaptic and it was 'bug city' !  I got it off my PC in a hurry.
Back to my faithful NBR.

---

### Post by themarker0 on 2010-04-11
> **Otis Spunkmiyer said:**
> Is there a difference in loading LXDE from Alt-F2 update as oppose to what's in Synaptic ?
I did Synaptic and it was 'bug city' !  I got it off my PC in a hurry.
Back to my faithful NBR.

I don't know whats Alt-F2. But what i did was load every LXDE package there.

---

### Post by Otis Spunkmiyer on 2010-04-11
How's it running ?  And what did you upgrade from, I mean was it full desktop Ubuntu 9.10 ?
It just gave me a few scares because it locked up on me a few times, then I could not get back into NBR.   When trying to figure out the task bar and to load at least a WiFI icon, that never happen.   I realize it's still Beta, but I'm relive I got out of it.
(without any damage to my NBR set up)

---

### Post by themarker0 on 2010-04-11
> **Otis Spunkmiyer said:**
> How's it running ?  And what did you upgrade from, I mean was it full desktop Ubuntu 9.10 ?
It just gave me a few scares because it locked up on me a few times, then I could not get back into NBR.   When trying to figure out the task bar and to load at least a WiFI icon, that never happen.   I realize it's still Beta, but I'm relive I got out of it.
(without any damage to my NBR set up)

Well so far its running great. The only thing thats bugged me that last couple weeks it the mouse and webcam, but thats for another time to fix. If you need any help getting yours working, your welcome to PM me. I'm not sure how much help i can be, but i'm happy to help when i can.

---

### Post by Otis Spunkmiyer on 2010-04-11
Thank you, I appreciate that.
'I might' try it again when full stable release is out.  Curiosity got the better of me.  I finally got my NBR set up, 'sweet'.
And man, I damn near had a heart attack.

---

### Post by themarker0 on 2010-04-11
> **Otis Spunkmiyer said:**
> Thank you, I appreciate that.
'I might' try it again when full stable release is out.  Curiosity got the better of me.  I finally got my NBR set up, 'sweet'.
And man, I damn near had a heart attack.

I know the same feeling, how much extra space do you have? If you want you could try a new partition off of that? Psumi wrote this great little post that i followed (Minus the minimal cd since that didn't work) It might work for you. 
[http://ubuntuforums.org/showpost.php?p=8754516&postcount=3](http://ubuntuforums.org/showpost.php?p=8754516&postcount=3)

---

