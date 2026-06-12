---
title: "How to completely remove Gnome desktop from Xfce?"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Narcoleptic_Insomniac on 2008-12-24
Hello, I recently installed Ubuntu 8.10 and discovered that it lagged the hell out of my computer whenever I tried to run pidgin, so I decided to try installing Xubuntu which worked excellent for me in the past, so I did the whole sudo apt-get install xubuntu-desktop deal and now I'm on xubuntu. But I just want to remove all of the old ubuntu gnome desktop so that its not hogging up all my memory. What would you recommend I do? Thank you in advance for the help.

---

### Post by halitech on 2008-12-24
check out the info here

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by w4ett on 2008-12-24
from: [http://www.psychocats.net/ubuntu/purexfcehardy](http://www.psychocats.net/ubuntu/purexfcehardy)
```

sudo apt-get remove alacarte bluez-gnome brltty brltty-x11 bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gedit gedit-common gimp-gnomevfs gimp-python gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools gtkhtml3.14 gvfs gvfs-backends gvfs-fuse hwtest hwtest-gtk launchpad-integration libalut0 libao2 libarchive1 libart2.0-cil libcdio-cdda0 libcdio-paranoia0 libcompizconfig0 libcurl3 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libglade2.0-cil libglew1.5 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpgme11 libgpod-common libgpod3 libgtk2.0-cil libgtkhtml3.14-19 libgtkhtml3.16-cil libgtksourceview2.0-0 libgtksourceview2.0-common libgvfscommon0 libgweather-common libgweather1 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp7 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libopenal0a libopenobex1 libpam-gnome-keyring libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpth20 libpulsecore5 librarian0 libsamplerate0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libsmbclient libsoup2.4-1 libsqlite0 libtracker-gtk0 libvorbisfile3 libwpg-0.1-1 libwps-0.1-1 libx11-xcb1 libxml2-utils mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share o3read obex-data-server openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-gmenu python-gtksourceview2 python-uno rdesktop rhythmbox rss-glx scim-bridge-agent scim-bridge-client-gtk seahorse sound-juicer sqlite sqlite3 ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc xulrunner-1.9-gnome-support yelp && sudo apt-get install xubuntu-desktop
```

Should work on on Intrepid too.

---

### Post by w4ett on 2008-12-24
Darn Halitech...ya beat me to it

---

### Post by Narcoleptic_Insomniac on 2008-12-24
> **halitech said:**
> check out the info here

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Are you from Halifax, Nova Scotia? I am to. And thank you for the help.

---

### Post by halitech on 2008-12-24
> **Narcoleptic_Insomniac said:**
> Are you from Halifax, Nova Scotia? I am to. And thank you for the help.

did the name give it away? ;) yes I am although originally from the valley, been up here for almost 5 years.

Very welcome and Merry Christmas

---

