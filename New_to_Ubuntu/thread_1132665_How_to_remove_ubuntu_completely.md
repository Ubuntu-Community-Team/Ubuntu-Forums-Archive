---
title: "How to remove ubuntu completely?"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Naz_Farooq on 2009-04-22
Hi guys,
I have been using ubuntu 8.10 intrepid for last 5 months on its own partition (16 gb). I am running windows XP as well as a second OS. I want to remove Ubuntu 8.10 completely and install Kubuntu in place of it. How would I do that. I have never thought of removing my ubuntu 8.10 but because of error in upgrading to Jaunty made me doing so.
Now I want to install Kubuntu 9.04. Can anyone help me for that.
Thanks in advance.

---

### Post by Peter09 on 2009-04-22
Well, as a start do the install and when you come to partitioning direct the install to use the old Ubuntu partitions.

---

### Post by billgoldberg on 2009-04-22
Fist and foreall, back up all the data you need.

Burn the Kubuntu cd.

During the installation process, put it over the existing Ubuntu installation (advanced mode).

---

### Post by sahabcse on 2009-04-22
Hi

Remove the old partition on installation tim then recreate it and install or find out the partition in windows and go to the disk manager and delete the partition.

---

### Post by Paqman on 2009-04-22
As long as your current install is still working, you don't need to reinstall at all Naz_Farooq. All you have to do is install the KDE desktop and remove the Gnome one.

You can do both steps by copying and pasting this command into the terminal:
```

sudo apt-get update && sudo apt-get remove alacarte app-install-data-commercial apport-gtk apturl at-spi binfmt-support bluez-gnome brasero brltty-x11 capplets-data cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet desktop-file-utils dmz-cursor-theme doc-base docbook-xml ekiga eog espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk jockey-gtk language-selector libart2.0-cil libasound2-plugins libatspi1.0-0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcompizconfig0 libcryptui0 libdecoration0 libdeskbar-tracker libdmx1 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libespeak1 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3 libgail-gnome-module libgamin0 libgconf2-4 libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglew1.5 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-desktop-2-7 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgpod3 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkglext1 libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libjpeg-progs libkpathsea4 liblaunchpad-integration1 liblircclient0 liblpint-bonobo0 libmbca0 libmeanwhile1 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-4 libopal-2.2 libopenobex1 liborbit2 libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gnome0 libpoppler-glib3 libportaudio0 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulse-browse0 libpulsecore5 libpurple-bin libpurple0 librarian0 librsvg2-common libschroedinger-1.0-0 libscim8c2a libsexy2 libshout3 libsilc-1.1-2 libsndfile1 libsoup2.4-1 libspeexdsp1 libsqlite0 libstartup-notification0 libtie-ixhash-perl libtotem-plparser12 libtracker-gtk0 libtrackerclient0 libuuid-perl libv4l-0 libvte-common libvte9 libwnck-common libwnck22 libwv-1.2-3 libx11-xcb1 libxevie1 libxml-twig-perl libxml-xpath-perl libxml2-utils libxres1 libzephyr3 metacity metacity-common mobile-broadband-provider-info mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon obex-data-server onboard openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pidgin-otr pkg-config policykit-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-beagle python-brlapi python-cairo python-gconf python-gdata python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-gtksourceview2 python-launchpad-integration python-notify python-numeric python-pkg-resources python-pyatspi python-pyorbit python-rdflib python-sexy python-virtkey python-vte rarian-compat rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket screen-resolution-extra screensaver-default-images seahorse seahorse-plugins sgml-data software-properties-gtk sqlite sqlite3 ssh-askpass-gnome synaptic syslinux system-config-printer-gnome system-tools-backends tangerine-icon-theme tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool tracker-utils transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers untex update-manager update-notifier usb-creator vinagre vino whois wv xbase-clients xbitmaps xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xterm xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity && sudo apt-get install kubuntu-desktop

```

---

### Post by Naz_Farooq on 2009-04-22
> **sahabcse said:**
> Hi

Remove the old partition on installation tim then recreate it and install or find out the partition in windows and go to the disk manager and delete the partition.

I don't want to remove the partition because if I do so I will lose all my data.

---

### Post by jolx on 2009-04-22
> **paqman said:**
> as long as your current install is still working, you don't need to reinstall at all naz_farooq. All you have to do is install the kde desktop and remove the gnome one.

You can do both steps by copying and pasting this command into the terminal:
```

sudo apt-get update && sudo apt-get remove alacarte app-install-data-commercial apport-gtk apturl at-spi binfmt-support bluez-gnome brasero brltty-x11 capplets-data cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet desktop-file-utils dmz-cursor-theme doc-base docbook-xml ekiga eog espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk jockey-gtk language-selector libart2.0-cil libasound2-plugins libatspi1.0-0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcompizconfig0 libcryptui0 libdecoration0 libdeskbar-tracker libdmx1 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libespeak1 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3 libgail-gnome-module libgamin0 libgconf2-4 libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglew1.5 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-desktop-2-7 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgpod3 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkglext1 libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libjpeg-progs libkpathsea4 liblaunchpad-integration1 liblircclient0 liblpint-bonobo0 libmbca0 libmeanwhile1 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-4 libopal-2.2 libopenobex1 liborbit2 libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gnome0 libpoppler-glib3 libportaudio0 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulse-browse0 libpulsecore5 libpurple-bin libpurple0 librarian0 librsvg2-common libschroedinger-1.0-0 libscim8c2a libsexy2 libshout3 libsilc-1.1-2 libsndfile1 libsoup2.4-1 libspeexdsp1 libsqlite0 libstartup-notification0 libtie-ixhash-perl libtotem-plparser12 libtracker-gtk0 libtrackerclient0 libuuid-perl libv4l-0 libvte-common libvte9 libwnck-common libwnck22 libwv-1.2-3 libx11-xcb1 libxevie1 libxml-twig-perl libxml-xpath-perl libxml2-utils libxres1 libzephyr3 metacity metacity-common mobile-broadband-provider-info mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon obex-data-server onboard openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pidgin-otr pkg-config policykit-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-beagle python-brlapi python-cairo python-gconf python-gdata python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-gtksourceview2 python-launchpad-integration python-notify python-numeric python-pkg-resources python-pyatspi python-pyorbit python-rdflib python-sexy python-virtkey python-vte rarian-compat rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket screen-resolution-extra screensaver-default-images seahorse seahorse-plugins sgml-data software-properties-gtk sqlite sqlite3 ssh-askpass-gnome synaptic syslinux system-config-printer-gnome system-tools-backends tangerine-icon-theme tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool tracker-utils transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers untex update-manager update-notifier usb-creator vinagre vino whois wv xbase-clients xbitmaps xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xterm xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity && sudo apt-get install kubuntu-desktop

```

+1

---

### Post by Naz_Farooq on 2009-04-22
> **Paqman said:**
> As long as your current install is still working, you don't need to reinstall at all Naz_Farooq. All you have to do is install the KDE desktop and remove the Gnome one.

You can do both steps by copying and pasting this command into the terminal:
```

sudo apt-get update && sudo apt-get remove alacarte app-install-data-commercial apport-gtk apturl at-spi binfmt-support bluez-gnome brasero brltty-x11 capplets-data cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet desktop-file-utils dmz-cursor-theme doc-base docbook-xml ekiga eog espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk jockey-gtk language-selector libart2.0-cil libasound2-plugins libatspi1.0-0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcompizconfig0 libcryptui0 libdecoration0 libdeskbar-tracker libdmx1 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libespeak1 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3 libgail-gnome-module libgamin0 libgconf2-4 libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglew1.5 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-desktop-2-7 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgpod3 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkglext1 libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libjpeg-progs libkpathsea4 liblaunchpad-integration1 liblircclient0 liblpint-bonobo0 libmbca0 libmeanwhile1 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-4 libopal-2.2 libopenobex1 liborbit2 libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gnome0 libpoppler-glib3 libportaudio0 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulse-browse0 libpulsecore5 libpurple-bin libpurple0 librarian0 librsvg2-common libschroedinger-1.0-0 libscim8c2a libsexy2 libshout3 libsilc-1.1-2 libsndfile1 libsoup2.4-1 libspeexdsp1 libsqlite0 libstartup-notification0 libtie-ixhash-perl libtotem-plparser12 libtracker-gtk0 libtrackerclient0 libuuid-perl libv4l-0 libvte-common libvte9 libwnck-common libwnck22 libwv-1.2-3 libx11-xcb1 libxevie1 libxml-twig-perl libxml-xpath-perl libxml2-utils libxres1 libzephyr3 metacity metacity-common mobile-broadband-provider-info mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon obex-data-server onboard openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pidgin-otr pkg-config policykit-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-beagle python-brlapi python-cairo python-gconf python-gdata python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-gtksourceview2 python-launchpad-integration python-notify python-numeric python-pkg-resources python-pyatspi python-pyorbit python-rdflib python-sexy python-virtkey python-vte rarian-compat rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket screen-resolution-extra screensaver-default-images seahorse seahorse-plugins sgml-data software-properties-gtk sqlite sqlite3 ssh-askpass-gnome synaptic syslinux system-config-printer-gnome system-tools-backends tangerine-icon-theme tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool tracker-utils transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers untex update-manager update-notifier usb-creator vinagre vino whois wv xbase-clients xbitmaps xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xterm xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity && sudo apt-get install kubuntu-desktop

```

Thank You very much. But I have tried it before and the result is shown in the attached picture. And I want to upgrade my OS to 9.04 as well. If I install Kubuntu 8.10, I can easily upgrade it to 9.04. I have Ubuntu 8.10 and I want to upgrade it to Jaunty 9.04 but cannot do so because Jaunty does not support my graphic card and 3D effects will not be working with it. Another thing is that I don't have enough space for upgrading it as well.
Could you please tell me how to remove Ubuntu 8.10 from my system. I want to install fresh Kubuntu 8.10.

---

### Post by jolx on 2009-04-22
> **Naz_Farooq said:**
> Thank You very much. But I have tried it before and the result is shown in the attached picture. And I want to upgrade my OS to 9.04 as well. If I install Kubuntu 8.10, I can easily upgrade it to 9.04. I have Ubuntu 8.10 and I want to upgrade it to Jaunty 9.04 but cannot do so because Jaunty does not support my graphic card and 3D effects will not be working with it. Another thing is that I don't have enough space for upgrading it as well.
Could you please tell me how to remove Ubuntu 8.10 from my system. I want to install fresh Kubuntu 8.10.

Where's the pic? :)

1. backup

2. install

---

### Post by Naz_Farooq on 2009-04-22
> **jolx said:**
> Where's the pic? :)

1. backup

2. install

Sorry ! Here is the picture.
What do you mean by 1. Back up 2. Install

---

### Post by lisati on 2009-04-22
> **Naz_Farooq said:**
> What do you mean by 1. Back up 2. Install

Make a backup copy of your important data before you proceed with the installation.

---

### Post by lkraemer on 2009-04-22
Naz_Farooq,
You are being told to BACKUP your important data.  To DVD, CDR, another harddrive or a server somewhere.  Then install from LiveCD the distro of
your choice, and use the old Ubuntu partition, by overwriting with the new
distro.  Then restore your data to the fresh install.

lkraemer

---

### Post by jolx on 2009-04-22
> **Naz_Farooq said:**
> Sorry ! Here is the picture.

maybe you could try disabling ppa1

---

### Post by Naz_Farooq on 2009-04-22
> **lisati said:**
> Make a backup copy of your important data before you proceed with the installation.

ok. If I am not removing partition should I back up my data. I have saved my data in my D:/ which is fat32 and I am using it for both Windows and Linux. I have started this
[c] sudo apt-get update && sudo apt-get remove alacarte app-install-data-commercial apport-gtk apturl at-spi binfmt-support bluez-gnome brasero brltty-x11 capplets-data cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet desktop-file-utils dmz-cursor-theme doc-base docbook-xml ekiga eog espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk jockey-gtk language-selector libart2.0-cil libasound2-plugins libatspi1.0-0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcompizconfig0 libcryptui0 libdecoration0 libdeskbar-tracker libdmx1 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libespeak1 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3 libgail-gnome-module libgamin0 libgconf2-4 libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglew1.5 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-desktop-2-7 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgpod3 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkglext1 libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libjpeg-progs libkpathsea4 liblaunchpad-integration1 liblircclient0 liblpint-bonobo0 libmbca0 libmeanwhile1 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-4 libopal-2.2 libopenobex1 liborbit2 libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gnome0 libpoppler-glib3 libportaudio0 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulse-browse0 libpulsecore5 libpurple-bin libpurple0 librarian0 librsvg2-common libschroedinger-1.0-0 libscim8c2a libsexy2 libshout3 libsilc-1.1-2 libsndfile1 libsoup2.4-1 libspeexdsp1 libsqlite0 libstartup-notification0 libtie-ixhash-perl libtotem-plparser12 libtracker-gtk0 libtrackerclient0 libuuid-perl libv4l-0 libvte-common libvte9 libwnck-common libwnck22 libwv-1.2-3 libx11-xcb1 libxevie1 libxml-twig-perl libxml-xpath-perl libxml2-utils libxres1 libzephyr3 metacity metacity-common mobile-broadband-provider-info mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon obex-data-server onboard openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pidgin-otr pkg-config policykit-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-beagle python-brlapi python-cairo python-gconf python-gdata python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-gtksourceview2 python-launchpad-integration python-notify python-numeric python-pkg-resources python-pyatspi python-pyorbit python-rdflib python-sexy python-virtkey python-vte rarian-compat rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket screen-resolution-extra screensaver-default-images seahorse seahorse-plugins sgml-data software-properties-gtk sqlite sqlite3 ssh-askpass-gnome synaptic syslinux system-config-printer-gnome system-tools-backends tangerine-icon-theme tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool tracker-utils transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers untex update-manager update-notifier usb-creator vinagre vino whois wv xbase-clients xbitmaps xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xterm xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity && sudo apt-get install kubuntu-desktop [/c]
and it is removing app. now

---

### Post by jolx on 2009-04-22
> **Naz_Farooq said:**
> ok. If I am not removing partition should I back up my data.

I do, just in case something goes wrong.

but if it was too annoying/time consuming, then i wouldn't.

of course you can always do what you want.

---

### Post by Naz_Farooq on 2009-04-22
> **jolx said:**
> I do, just in case something goes wrong.

but if it was too annoying/time consuming, then i wouldn't.

of course you can always do what you want.

Now nothing is happening. Oh my God. I cannot start ubuntu now and it is not booting as well.
It is showing a blank screen and something written like this

"Ubuntu 8.10 nazfarooq-laptop tty1
nazfarooq-laptop login:"

and when I log in it gives me this

"Last login: Wed Apr 22 15:22:28 GST 2009 on tty1
Linux nazfarooq-laptop 2.6.27.11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.
Ubuntu comes with Absolutely NO WARRANTY, to the extent permitted by
application law.
To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
You have new mail.
nazfarooq@nazfarooq-laptop:~$"

What to do now. I have made a mess I think.
Please help.

---

### Post by halitech on 2009-04-22
> **Naz_Farooq said:**
> Thank You very much. But I have tried it before and the result is shown in the attached picture. And I want to upgrade my OS to 9.04 as well. If I install Kubuntu 8.10, I can easily upgrade it to 9.04. I have Ubuntu 8.10 and I want to upgrade it to Jaunty 9.04 but cannot do so because Jaunty does not support my graphic card and 3D effects will not be working with it. Another thing is that I don't have enough space for upgrading it as well.
Could you please tell me how to remove Ubuntu 8.10 from my system. I want to install fresh Kubuntu 8.10.

maybe I'm not understanding something here but you say Jaunty doesn't support your card so you want to install Kubuntu 9.04. Kubuntu 9.04 IS Jaunty with KDE for a desktop instead of gnome so why do you think Kubuntu 9.04 will support your video card if Ubuntu 9.04 doesn't support your card?

> Now nothing is happening. Oh my God. I cannot start ubuntu now and it is not booting as well.
It is showing a blank screen and something written like this

"Ubuntu 8.10 nazfarooq-laptop tty1
nazfarooq-laptop login:"

looks like 8.10 didn't do such a good job of supporting your video card either and dropped you to a command line after the install. Can you give us the output of
```
lspic -C video
``` so we can see what video card you have and how to help you out.

---

### Post by Naz_Farooq on 2009-04-22
> **halitech said:**
> maybe I'm not understanding something here but you say Jaunty doesn't support your card so you want to install Kubuntu 9.04. Kubuntu 9.04 IS Jaunty with KDE for a desktop instead of gnome so why do you think Kubuntu 9.04 will support your video card if Ubuntu 9.04 doesn't support your card?



looks like 8.10 didn't do such a good job of supporting your video card either and dropped you to a command line after the install. Can you give us the output of
```
lspic -C video
``` so we can see what video card you have and how to help you out.

Sorry dear,
I have formatted the partition in which I have been using ubuntu 8.10. Now I have only one OS windows XP and now I am installing Kubuntu 8.10 within windows but in a different partition. I don't know what has gone wrong but in WindowsXP I cannot shut down my system or restart it. I am installing Kubuntu 8.10 within WindowsXP. Let see what happens now. How can I make my system restart or shut down using WindowsXP?
Help !

---

### Post by lkraemer on 2009-04-22
Naz_Faroog,
Why don't you download a copy of supergrub and use it to restore the 
MBR (Master Boot Record) of Windows XP so you at least can boot XP
properly.  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

Or use Ultimate Boot CD (UBCD) or SystemRescueCD to boot the XP partition.
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Then when you have XP working, Install your new Distro.  I wouldn't
install it inside XP, but that is my opinon.  I'd rather have it in it's
own partition, for easy of deleting etc.

lkraemer

---

