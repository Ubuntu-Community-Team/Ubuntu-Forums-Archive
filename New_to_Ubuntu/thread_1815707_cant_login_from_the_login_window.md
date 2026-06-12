---
title: "cant login from the login window?"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by 007casper on 2011-07-31
trouble logining from the start window.

I default to console login.  It takes the username, and password.  However, I cant seem to login from KDE.

Is there a corrupted file?  How come I cant login???

---

### Post by Redblade20XX on 2011-07-31
What do you mean? Is there a gui login screen or does it not work?

Take a look at this page, specifically section 5

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by 007casper on 2011-08-01
there is a gui login window.  If I put username, and password, it just doesnt work.  

Then, I picked console login.  I was able to get into the system.

??

---

### Post by 007casper on 2011-08-03
> Take a look at this page, specifically section 5

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

maybe the solution is on the page, but I dont see it. 

I am trying to figure how come I can login via console, but not gui interface with the same credentials.

???

---

### Post by smurphy_it on 2011-08-03
I had a similar problem.  Had to do with an external monitor connected to my port replicator.  If the external was connected it would accept username/password, start to login, then revert back to login screen.

If you don't have that setup, then yeah it's probably something corrupt within your $HOME directory.  I'd probably start with rename the $HOME/.gconf directory

```
mv ~/.gconf ~/.gconf.old
```

Then attempt to login.

---

### Post by Genuin on 2011-08-07
The same problem here. I run out of disk space in / and can't login anymore into KDE, even after freeing up a few Gb of disk space.

Whenever I put username and password in the graphical login window it disappears for a second while a stripped, distorted pattern appears in the background, and then login screen again. I can log in using console mode and launch KDE with startx, though.

Renaming ~/.gonf doesn't solve it. I'm a noob but can't find anything strongly suspicious in the logs. 

Please HELP! I've read several threads with similar login problems in which people give up and reinstall the system, but it would be rather painful in my case.


tail -30 ~/.xsession-errors
```
Xsession: X session started for ahc at dom ago  7 12:40:24 CEST 2011
konsole(3014)/kdeui (kdelibs): Attempt to use QAction "change-profile" with KXMLGUIFactory!
x-terminal-emulator: Fatal IO error: client killed
kDebugStream called after destruction (from virtual Konsole::SessionManager::~SessionManager() file ../../../../apps/konsole/src/SessionManager.cpp line 301)
Konsole SessionManager destroyed with sessions still alive
```tail -30 /var/log/Xorg.0.log
```
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) NOUVEAU(0): NVLeaveVT is called.
(II) NOUVEAU(0): Closed GPU channel 1
 ddxSigGiveUp: Closing log
```tail -30 kdm.log
```
Current Operating System: Linux pccasa 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686
Kernel command line: root=UUID=91853500-df36-47d4-a9b0-5fba7cf62afd ro quiet splash
Build Date: 10 December 2010  05:53:04PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug  7 12:40:18 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
resize called 1280 800
QFont::fromString: Invalid description 'Serif,20,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,75,0'
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /tmp/1332871117/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address.
IBusInputContext::createInputContext: no connection to ibus-daemon
resize called 1280 800
QFont::fromString: Invalid description 'Serif,20,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,75,0'
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero o el directorio
QFileSystemWatcher: failed to add paths: /tmp/0572586660/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address.
IBusInputContext::createInputContext: no connection to ibus-daemon
 ddxSigGiveUp: Closing log
```

---

### Post by SeijiSensei on 2011-08-07
See if this helps.  Log into the terminal as you did before, navigate to your home directory, and enter "mv .kde .kde.bad".  Now logout and reboot.  That will force KDE to rebuild your configuration from scratch.  Does that solve the problem?  If so, you'll need to rebuild your desktop to match what you had before.  Consult the files in .kde.bad/share/config to see the configurations you had created before.

.gconf is where GNOME configuration files reside; they're not relevant to a KDE desktop.

I encountered this problem in an earlier version of KDE, but moving to 10.10 solved it for me.  The implementation of KDE in 10.04 was rather buggy, but 10.10 has been rock solid.

---

### Post by 007casper on 2011-08-07
reloaded 10.4 then upgraded to 10.10 ubuntu then removed gnome, and install kde

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

```
sudo apt-get remove adium-theme-ubuntu aisleriot alacarte app-install-data-partner apport-gtk aptdaemon aptdaemon-data at-spi bamfdaemon banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore baobab binfmt-support bluez-gstreamer bogofilter bogofilter-bdb bogofilter-common branding-ubuntu brasero brasero-cdrkit brasero-common brltty-x11 build-essential capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-main compizconfig-backend-gconf computer-janitor computer-janitor-gtk desktop-file-utils diffstat dmz-cursor-theme doc-base dpkg-dev empathy empathy-common eog espeak espeak-data evince evince-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content fakeroot file-roller firefox firefox-globalmenu firefox-gnome-support g++ g++-4.5 gamin gbrainy gcalctool gcc gcc-4.5 gconf-defaults-service gconf-editor gdm gdm-guest-session gedit gedit-common geoclue geoclue-ubuntu-geoip gettext ginn gir1.2-appindicator-0.1 gir1.2-atk-1.0 gir1.2-freedesktop gir1.2-gconf-2.0 gir1.2-gdkpixbuf-2.0 gir1.2-gtk-2.0 gir1.2-notify-0.7 gir1.2-panelapplet-3.0 gir1.2-pango-1.0 gir1.2-soup-2.4 gir1.2-vte-0.0 gksu gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games-common gnome-icon-theme gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-bonobo gnome-panel-data gnome-power-manager gnome-screensaver gnome-screenshot gnome-search-tool gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-log gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-user-share gnome-utils-common gnomine gsettings-desktop-schemas gstreamer0.10-gnonlin gstreamer0.10-nice gstreamer0.10-plugins-base-apps gstreamer0.10-tools gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-fuse gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter humanity-icon-theme hwdata ibus ibus-gtk ibus-pinyin ibus-pinyin-db-android ibus-pinyin-db-open-phrase ibus-table indicator-applet indicator-applet-appmenu indicator-applet-complete indicator-applet-session indicator-application indicator-appmenu indicator-datetime indicator-me indicator-messages indicator-session indicator-sound intltool-debian jockey-gtk language-selector-gnome launchpad-integration libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libappindicator0.1-cil libappindicator1 libapt-pkg-perl libart-2.0-2 libart2.0-cil libatkmm-1.6-1 libatspi1.0-0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libbamf0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libboost-serialization1.42.0 libbrasero-media1 libburn4 libc-dev-bin libc6-dev libcairo-gobject2 libcairo-perl libcairomm-1.0-1 libcamel1.2-19 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcdio-cdda0 libcdio-paranoia0 libcdio10 libclass-accessor-perl libcompizconfig0 libcroco3 libcryptui0 libdconf0 libdecoration0 libdee-1.0-1 libdigest-hmac-perl libdotconf1.0 libdpkg-perl libebackend1.2-0 libebook1.2-10 libecal1.2-8 libedata-book1.2-8 libedata-cal1.2-10 libedataserver1.2-14 libedataserverui1.2-11 libegroupwise1.2-13 libemail-valid-perl libept1 libespeak1 libevdocument3 libevent-1.4-2 libevolution libevview3 libexempi3 libfolks-telepathy22 libfolks22 libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2.0-cil libgcr0 libgd2-xpm libgdata-common libgdata1.7-cil libgdata11 libgdu-gtk0 libgdu0 libgee2 libgeoclue0 libgexiv2-0 libgkeyfile1.0-cil libgksu2-0 libglade2-0 libglade2.0-cil libgladeui-1-11 libglew1.5 libglewmx1.5 libglib-perl libglib2.0-bin libglib2.0-cil libglib2.0-data libglibmm-2.4-1c2a libgmime-2.4-2 libgmime2.4-cil libgnome-bluetooth8 libgnome-desktop-2-17 libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-common libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgoocanvas-common libgoocanvas3 libgp11-0 libgsl0ldbl libgssdp-1.0-2 libgstfarsight0.10-0 libgtk-sharp-beans-cil libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgudev1.0-cil libgupnp-1.0-3 libgupnp-igd-1.0-3 libgvfscommon0 libgweather-common libgweather1 libgwibber1 libibus2 libido-0.1-0 libindicate-gtk2 libindicator3 libio-pty-perl libio-string-perl libipc-run-perl libisofs6 libjson-glib-1.0-0 libkpathsea5 liblaunchpad-integration-common liblaunchpad-integration1 liblaunchpad-integration1.0-cil liblircclient0 liblouis-data liblouis2 liblua5.1-0 libmetacity-private0 libmission-control-plugins0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil libmono-management2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-system2.0-cil libmono-zeroconf1.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libnice10 libnotify0.4-cil libnotify1 libnotify4 libnux-0.9-0 libnux-0.9-common liboobs-1-5 libopencc1 liboverlay-scrollbar-0.1-0 libpam-gnome-keyring libpanel-applet-3-0 libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libparse-debianchangelog-perl libpolkit-gtk-1-0 libpoppler-glib6 libportaudio2 libprotobuf6 libprotoc6 libpst4 libpurple-bin libpurple0 libquvi0 librarian0 libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-style-human librsvg2-2 librsvg2-common libsdl1.2debian libsdl1.2debian-pulseaudio libsigc++-2.0-0c2a libsilc-1.1-2 libsilcclient-1.1-3 libspeechd2 libstartup-notification0 libstdc++6-4.5-dev libsub-name-perl libsyncdaemon-1.0-1 libt1-5 libtaglib2.0-cil libtelepathy-farsight0 libtelepathy-glib0 libtelepathy-logger2 libtie-ixhash-perl libtotem-plparser17 libubuntuone-1.0-1 libubuntuone1.0-cil libunique-1.0-0 libunistring0 libunity-misc0 libunity4 libutouch-geis1 libuuid-perl libvte-common libvte9 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwmf0.2-7 libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-event1 libxklavier16 libxml-twig-perl libxml-xpath-perl libxres1 libzeitgeist-1.0-1 libzephyr4 light-themes lintian linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic linux-headers-generic linux-libc-dev lzma make manpages-dev media-player-info metacity metacity-common mono-2.0-gac mono-csharp-shell mono-gac mono-gmcs mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share network-manager-gnome network-manager-pptp-gnome notification-daemon notify-osd notify-osd-icons nux-tools onboard overlay-scrollbar patch pinyin-database pitivi pkg-config plymouth-theme-ubuntu-logo policykit-1-gnome protobuf-compiler pulseaudio-module-gconf python-appindicator python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-argparse python-brlapi python-configglue python-defer python-egenix-mxdatetime python-egenix-mxtools python-farsight python-gconf python-glade2 python-gmenu python-gnome2 python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-gtkspell python-ibus python-indicate python-launchpad-integration python-libproxy python-libxml2 python-louis python-mako python-markupsafe python-notify python-openssl python-pam python-papyon python-piston-mini-client python-protobuf python-pyatspi python-pygoocanvas python-pyinotify python-pyorbit python-rdflib python-serial python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit python-wnck rarian-compat screensaver-default-images seahorse sessioninstaller shotwell simple-scan software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-sso-client ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-gtk unity unity-asset-pool unity-common unity-place-applications unity-place-files update-manager update-notifier update-notifier-common usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xscreensaver-data xscreensaver-gl xsltproc xul-ext-ubufox yelp yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zeitgeist-extension-fts zenity && sudo apt-get install kubuntu-desktop
```

same annoying problem

cant login from the gui kde interface.  However I can from the terminal.

---

### Post by 007casper on 2011-08-07
how do I remove kde and reinstall gnome?

It totally worked on gnome before without any problems

---

### Post by MartyBuntu on 2011-08-07
> **007casper said:**
> 

cant login from the gui kde interface.  However I can from the terminal.

In the login drop down list, is there an entry for **plasma-desktop**?

---

### Post by Genuin on 2011-08-08
> **SeijiSensei said:**
> See if this helps.  Log into the terminal as you did before, navigate to your home directory, and enter "mv .kde .kde.bad".  Now logout and reboot.  That will force KDE to rebuild your configuration from scratch.  Does that solve the problem?  If so, you'll need to rebuild your desktop to match what you had before.  Consult the files in .kde.bad/share/config to see the configurations you had created before.

.gconf is where GNOME configuration files reside; they're not relevant to a KDE desktop.

I encountered this problem in an earlier version of KDE, but moving to 10.10 solved it for me.  The implementation of KDE in 10.04 was rather buggy, but 10.10 has been rock solid.

Thanks for your help!
Renaming .kde doesn't solve the problem in my case. Nevertheless, I have created a new user account with adduser, and this user can log into KDE with no issues. After several reboots and login/logout of the dummy user, I still can't graphically log into KDE with the other account (console login + startx works fine).

I have tried to upgrade to 10.10 but another (unrelated?) problem arises and the upgrade is aborted:
```
Failed to fetch http://es.archive.ubuntu.com/ubuntu/pool/universe/c/coreutils/mktemp_8.5-1ubuntu3_all.deb 403  Forbidden
Failed to fetch http://es.archive.ubuntu.com/ubuntu/pool/universe/g/gnupg/gnupg-curl_1.4.10-2ubuntu2_i386.deb 403  Forbidden
```

---

### Post by 007casper on 2011-08-08
I just removed kde set up, and default back to 10.4 gnome.  Nothing else worked.  However, I didnt try to create another user on the terminal.  I just pull the plug on it.

---

### Post by Genuin on 2011-08-09
I just successfully upgraded to Kubuntu 10.10, but the problem doesn't go away.

There must be some config files outside of the .kde directory that are used for a graphical login, but not when console login + startx is used.

---

### Post by smurphy_it on 2011-08-15
If you had an "Encrypted Home Directory", that can cause login issues as well.  Sounds like the profile was messed up.

---

### Post by Genuin on 2011-08-21
> **smurphy_it said:**
> If you had an "Encrypted Home Directory", that can cause login issues as well.  Sounds like the profile was messed up.

I don't have an encrypted home directory or encrypted partitions, but definitely looks like a kde user-profile issue. I have installed the xfce4 desktop and works like a charm. I'll give it a try.

---

