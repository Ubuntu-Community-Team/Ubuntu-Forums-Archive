---
title: "apt-get remove - Some packages could not be installed?"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by mr_luksom on 2011-04-23
I've moved back to Xubuntu lately, and I decided it was time to remove all of the GNOME bits and piece from the initial Ubuntu install. I was following the psychocats guide ([http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)) for pure XFCE, however came across this preventing me from getting any further:

```


Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqtwebkit4 : Depends: phonon but it is not going to be installed


```

Struck me as a bit odd, as I was only using an 'apt-get remove' (as xubuntu-desktop is already installed I removed the last part of the line). Any ideas?

---

### Post by ptn107 on 2011-04-26
Unless you use one of the following packages:
[http://paste.ubuntu.com/599571/](http://paste.ubuntu.com/599571/)

then you don't need to install libqtwebkit4.

---

### Post by mr_luksom on 2011-04-28
I see, however the command I am issuing is a 'apt-get remove', and does not include libqtwebkit4. Why would it be complaining about me removing an unrelated package?

---

### Post by jtarin on 2011-04-28
What was the complete command you used to arrive at this result?

---

### Post by oldos2er on 2011-04-28
The command given at psychocats.net is ```
sudo apt-get remove adium-theme-ubuntu alacarte at-spi baobab binfmt-support bluez-gstreamer bogofilter bogofilter-bdb bogofilter-common branding-ubuntu brasero brasero-cdrkit brasero-common capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin desktopcouch dvd+rw-tools empathy empathy-common eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content exiv2 gbrainy gconf-defaults-service gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-bluetooth gnome-control-center gnome-dictionary gnome-disk-utility gnome-mag gnome-media gnome-media-common gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver gnome-screenshot gnome-search-tool gnome-session gnome-session-canberra gnome-session-common gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-utils gnome-utils-common gstreamer0.10-gnonlin gwibber gwibber-service indicator-applet indicator-applet-session indicator-me indicator-messages indicator-session indicator-sound libappindicator0.1-cil libart2.0-cil libbrasero-media1 libcamel1.2-14 libcanberra-pulse libcompizconfig0 libcouchdb-glib-1.0-2 libcryptui0 libcurl3 libdconf0 libdecoration0 libdesktopcouch-glib-1.0-2 libdmapsharing2 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13 libevolution libexempi3 libexiv2-6 libfolks-telepathy0 libfolks0 libgail-common libgail-gnome-module libgconf2.0-cil libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata7 libgdict-1.0-6 libgdu-gtk0 libgee2 libgexiv2-0 libglade2.0-cil libgladeui-1-9 libglib2.0-cil libglib2.0-data libgmime-2.4-2 libgmime2.4-cil libgnome-mag2 libgnome-media0 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.24-cil libgnomepanel2.24-cil libgoocanvas-common libgoocanvas3 libgpgme11 libgpod-common libgpod4 libgraphite3 libgsl0ldbl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtksourceview2.0-0 libgtksourceview2.0-common libgweather-common libgweather1 libgwibber0 libhyphen0 libical0 libido-0.1-0 liblaunchpad-integration1.0-cil liblircclient0 liblouis-data liblouis2 libmetacity-private0 libmission-control-plugins0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil libmono-management2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-system2.0-cil libmtp8 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27-gnutls libprotobuf6 libprotoc6 libpth20 libraptor1 librasqal2 librdf0 libsctp1 libsdl1.2debian libsdl1.2debian-pulseaudio libstlport4.6ldbl libsyncdaemon-1.0-1 libtelepathy-farsight0 libtelepathy-logger1 libtotem-plparser17 libubuntuone-1.0-1 libvala-0.10-0 libwmf0.2-7-gtk light-themes lksctp-tools media-player-info metacity metacity-common mono-2.0-gac mono-csharp-shell mono-gac mono-gmcs mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share obexd-client openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-math openoffice.org-style-galaxy openoffice.org-style-human openoffice.org-writer pitivi plymouth-theme-ubuntu-logo protobuf-compiler pulseaudio-module-bluetooth pulseaudio-module-gconf python-argparse python-avahi python-brlapi python-configglue python-couchdb python-crypto python-desktopcouch-records python-egenix-mxdatetime python-egenix-mxtools python-farsight python-gnomeapplet python-gtksourceview2 python-gtkspell python-indicate python-libproxy python-louis python-mako python-markupsafe python-papyon python-protobuf python-pyatspi python-pycurl python-pygoocanvas python-pyinotify python-rdflib python-speechd python-telepathy python-twisted-names python-ubuntuone python-ubuntuone-client python-ubuntuone-storageprotocol python-uno python-wnck rdesktop rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store screen-resolution-extra seahorse shotwell ssh-askpass-gnome telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome uno-libs3 ure vino whois wodim xfonts-mathml && sudo apt-get install xubuntu-desktop
```

Perhaps the OP had KDE installed at one time, since libqtwebkit4 is a Qt package.

---

### Post by mr_luksom on 2011-05-01
I did have KDE installed a while ago, but not anymore. Issue has gone away due to a clean install for other reasons, thanks for the help.

---

