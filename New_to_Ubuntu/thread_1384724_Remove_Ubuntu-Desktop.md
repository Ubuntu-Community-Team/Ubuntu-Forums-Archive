---
title: "Remove Ubuntu-Desktop"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by darkeye123 on 2010-01-18
Hey there,

I installed the Lubuntu-Desktop package a little while ago, and I would now like to only run LXDE on my system, instead of the default GNOME manager.

I know I could remove a majority of programs using sudo apt-get remove ubuntu-desktop, but I was wondering if that would break a ton of stuff.
Just wanted to ask first before I mess anything up royally :)

---

### Post by Bios Element on 2010-01-18
Yes, you can.

---

### Post by darkeye123 on 2010-01-18
Alright thanks!

Now one more question: when I do sudo apt-get remove ubuntu-desktop, it says that the package is not installed. 

I installed ubuntu off of the default CD, so I never installed ubuntu-destkop via command line... how would I remove it then?

---

### Post by zeroseven0183 on 2010-01-18
What you need to do there is to install ubuntu-desktop then remove it afterwards.

And to remove the packages:
```
sudo apt-get remove alacarte app-install-data-partner aptdaemon binfmt-support brltty brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktopcouch devicekit-power empathy empathy-doc eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-documentation-en evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot gconf-defaults-service gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-bluetooth gnome-control-center gnome-disk-utility gnome-media gnome-media-common gnome-menus gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session gnome-session-canberra gnome-settings-daemon gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools gvfs-fuse human-theme humanity-icon-theme ibus ibus-gtk ibus-m17n ibus-table indicator-applet indicator-applet-session indicator-messages indicator-session libanthy0 libart2.0-cil libcamel1.2-14 libcanberra-pulse libcolamd2.7.1 libcompizconfig0 libcouchdb-glib-1.0-1 libcryptui0 libdbusmenu-glib0 libdbusmenu-gtk0 libdecoration0 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libgconf2.0-cil libgd2-xpm libgdata-google1.2-1 libgdata1.2-1 libgdict-1.0-6 libgdiplus libgdu-gtk0 libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2a-cil libgnome-keyring1.0-cil libgnome-media0 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.24-cil libgnomepanel2.24-cil libgpod-common libgpod4 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtksourceview2.0-0 libgtksourceview2.0-common libgweather-common libgweather1 libhyphen0 libibus1 libical0 libjson-glib-1.0-0 liblpint-bonobo0 libm17n-0 libmetacity0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libmtp8 libmusicbrainz4c2a libmysqlclient16 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27-gnutls libotf0 libpisock9 libpisync1 libpq5 libprotobuf3 libpst4 libpulse-browse0 libpulse-mainloop-glib0 libraptor1 librasqal1 librdf0 libsctp1 libspeexdsp1 libsqlite0 libstlport4.6ldbl libtelepathy-farsight0 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7-gtk lksctp-tools lp-solve m17n-contrib m17n-db media-player-info mesa-utils metacity metacity-common mono-2.0-gac mono-gac mono-runtime mousetweaks mysql-common nautilus nautilus-data nautilus-sendto nautilus-share obexd-client openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-math openoffice.org-style-galaxy openoffice.org-style-human openoffice.org-writer pkg-config protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon-gtk python-avahi python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-fstab python-gmenu python-gnomeapplet python-gnomekeyring python-gtksourceview2 python-ibus python-openssl python-pam python-papyon python-protobuf python-pyinotify python-rsvg python-serial python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone-client python-ubuntuone-storageprotocol python-uno python-webkit raptor-utils rdesktop redland-utils rhythmbox screen-resolution-extra seahorse software-center ssh-askpass-gnome telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome uno-libs3 ure vino whois xdg-user-dirs-gtk xfonts-mathml && sudo apt-get install xubuntu-desktop
```

---

