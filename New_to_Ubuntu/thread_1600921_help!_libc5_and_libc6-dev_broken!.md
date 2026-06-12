---
title: "help! libc5 and libc6-dev broken!"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by kekearif on 2010-10-19
hey, just installed ubuntu 10... everything was fine then I installed skype. Next I decided to run the update manager and it returned a message saying I had 2 broken packages,,,,

If I go into the synaptic package manager I can see that libc6 and libc6-dev are broken :(

how can I fix these?

thanks

---

### Post by sikander3786 on 2010-10-19
Try

```
sudo apt-get install -f
```

And post back the output if any errors are reported.

---

### Post by kekearif on 2010-10-19
> **sikander3786 said:**
> Try

```
sudo apt-get install -f
```And post back the output if any errors are reported.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  acpi-support acpid adduser aisleriot alacarte alsa-base alsa-utils anacron
  apparmor apparmor-utils apport apport-gtk apt apt-transport-https apt-utils
  apt-xapian-index aptdaemon apturl apturl-common aspell aspell-en at at-spi
  avahi-autoipd avahi-daemon avahi-utils baobab base-files base-passwd bash
  bash-completion bc bind9-host binfmt-support binutils bluez bluez-alsa
  bluez-cups bluez-gstreamer bogofilter bogofilter-bdb brasero brasero-cdrkit
  brltty brltty-x11 bsdmainutils bsdutils busybox-initramfs byobu bzip2
  ca-certificates ca-certificates-java capplets-data checkbox checkbox-gtk
  cli-common command-not-found compiz compiz-core compiz-fusion-plugins-main
  compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor
  computer-janitor-gtk console-setup consolekit coreutils couchdb-bin cpio cpp
  cpp-4.4 cron cups cups-bsd cups-client cups-driver-gutenprint dash dbus
  dbus-x11 dc debconf debconf-i18n debianutils defoma desktop-file-utils
  desktopcouch dhcp3-client dhcp3-common dictionaries-common diffutils
  dmidecode dmsetup dnsmasq-base dnsutils doc-base docbook-xml dosfstools dpkg
  dvd+rw-tools e2fslibs e2fsprogs ed eject empathy eog erlang-base
  erlang-crypto erlang-inets erlang-mnesia erlang-public-key
  erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl espeak
  evince evolution evolution-couchdb evolution-data-server evolution-exchange
  evolution-indicator evolution-plugins evolution-webcal exiv2 fancontrol file
  file-roller findutils firefox firefox-branding firefox-gnome-support
  flashplugin-installer fontconfig fontconfig-config foo2zjs
  foomatic-db-compressed-ppds foomatic-db-engine foomatic-filters
  friendly-recovery ftp fuse-utils gamin gbrainy gcalctool gcc gcc-4.4
  gconf-defaults-service gconf-editor gconf2 gconf2-common gdb gdm
  gdm-guest-session gedit genisoimage gettext-base ghostscript
  ghostscript-cups ghostscript-x gir1.0-glib-2.0 gksu gnome-about
  gnome-accessibility-themes gnome-applets gnome-applets-data gnome-bluetooth
  gnome-codec-install gnome-control-center gnome-dictionary gnome-disk-utility
  gnome-doc-utils gnome-games-common gnome-icon-theme gnome-keyring gnome-mag
  gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-nettool
  gnome-orca gnome-panel gnome-panel-data gnome-power-manager
  gnome-screensaver gnome-screenshot gnome-search-tool gnome-session
  gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku
  gnome-system-log gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu
  gnome-user-guide gnome-user-guide-en gnome-utils gnomine gnupg gpgv grep
  groff-base grub-common grub-pc gstreamer0.10-alsa gstreamer0.10-ffmpeg
  gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-nice
  gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf
  gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-fuse gwibber
  gwibber-service gzip hdparm hostname hpijs hplip hplip-cups hplip-data
  humanity-icon-theme hunspell-en-ca hunspell-en-us ibus ibus-gtk ibus-pinyin
  ibus-table icedtea-6-jre-cacao icedtea6-plugin ifupdown indicator-applet
  indicator-applet-session indicator-application indicator-me
  indicator-messages indicator-session indicator-sound info initramfs-tools
  initramfs-tools-bin initscripts inputattach insserv install-info
  intel-gpu-tools iproute iptables iputils-arping iputils-ping
  iputils-tracepath irqbalance jockey-common jockey-gtk kbd kerneloops-daemon
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base language-selector language-selector-common
  language-support-en language-support-writing-en laptop-detect
  launchpad-integration less lftp liba52-0.7.4 libaa1 libaccess-bridge-java
  libaccess-bridge-java-jni libacl1 libapparmor-perl libapparmor1
  libappindicator0.1-cil libappindicator1 libarchive1 libart-2.0-2
  libart2.0-cil libasound2 libasound2-plugins libaspell15 libass4 libatasmart4
  libatk1.0-0 libatk1.0-data libatm1 libatspi1.0-0 libattr1 libaudio2
  libavahi-client3 libavahi-common3 libavahi-core7 libavahi-glib1
  libavahi-gobject0 libavahi-ui0 libavc1394-0 libavcodec52 libavformat52
  libavutil50 libbind9-60 libblkid1 libbluetooth3 libbonobo2-0 libbonoboui2-0
  libbrasero-media1 libbrlapi0.5 libbsd0 libburn4 libbz2-1.0 libc-dev-bin
  libc6 libc6-dev libcaca0 libcairo-perl libcairo2 libcairomm-1.0-1
  libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse
  libcanberra0 libcap-ng0 libcap2 libcdaudio1 libcdio-cdda0 libcdio-paranoia0
  libcdio10 libcdparanoia0 libcelt0-0 libck-connector0 libclutter-1.0-0
  libclutter-gtk-0.10-0 libcolamd2.7.1 libcomerr2 libcompizconfig0
  libcouchdb-glib-1.0-2 libcroco3 libcrypt-passwdmd5-perl libcryptui0 libcups2
  libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3
  libcurl3-gnutls libdaemon0 libdatrie1 libdb4.8 libdbus-1-3 libdbus-glib-1-2
  libdbusmenu-glib1 libdbusmenu-gtk1 libdc1394-22 libdca0 libdconf0
  libdecoration0 libdesktopcouch-glib-1.0-2 libdevmapper1.02.1
  libdigest-sha1-perl libdirac-encoder0 libdirectfb-1.2-9 libdjvulibre21
  libdmapsharing2 libdns66 libdotconf1.0 libdrm-intel1 libdrm-nouveau1
  libdrm-radeon1 libdrm2 libdv4 libdvdnav4 libdvdread4 libebackend1.2-0
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7
  libedataserver1.2-13 libedataserverui1.2-8 libedit2 libeggdbus-1-0
  libegroupwise1.2-13 libelf1 libenca0 libenchant1c2a libept1 libespeak1
  libevdocument3 libevent-1.4-2 libevolution libevview3 libexempi3 libexif12
  libexiv2-6 libexpat1 libfaad2 libffi5 libfftw3-3 libfile-copy-recursive-perl
  libflac8 libflite1 libfolks-telepathy0 libfolks0 libfont-afm-perl
  libfontconfig1 libfontenc1 libfreetype6 libfreezethaw-perl libfribidi0
  libfs6 libfuse2 libgadu3 libgail-common libgail-gnome-module libgail18
  libgamin0 libgc1c2 libgcc1 libgconf2-4 libgconf2.0-cil libgcr0 libgcrypt11
  libgd2-xpm libgdata-google1.2-1 libgdata1.2-1 libgdata7 libgdbm3
  libgdict-1.0-6 libgdk-pixbuf2.0-0 libgdu-gtk0 libgdu0 libgee2 libgeoip1
  libgexiv2-0 libgif4 libgirepository1.0-1 libgksu2-0 libgl1-mesa-dri
  libgl1-mesa-glx libglade2-0 libglade2.0-cil libgladeui-1-9 libglib-perl
  libglib2.0-0 libglib2.0-cil libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa
  libgme0 libgmime-2.4-2 libgmime2.4-cil libgmp3c2 libgnome-bluetooth8
  libgnome-desktop-2-17 libgnome-keyring0 libgnome-mag2 libgnome-media0
  libgnome-menu2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnome2.24-cil libgnomecanvas2-0 libgnomekbd-common libgnomekbd4
  libgnomepanel2.24-cil libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgnutls26 libgomp1 libgoocanvas3 libgp11-0
  libgpg-error0 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpm2
  libgpod-common libgpod4 libgraphite3 libgs8 libgsl0ldbl libgsm1
  libgssapi-krb5-2 libgssdp-1.0-2 libgstfarsight0.10-0
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk-vnc-1.0-0
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtkhtml-editor0
  libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtkspell0
  libgtop2-7 libgucharmap7 libgudev-1.0-0 libgupnp-1.0-3 libgupnp-igd-1.0-3
  libgutenprint2 libgvfscommon0 libgweather-common libgweather1 libgwibber0
  libhpmud0 libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhunspell-1.2-0 libhyphen0 libibus2 libical0 libice6
  libicu42 libid3tag0 libidl0 libidn11 libido-0.1-0 libiec61883-0
  libieee1284-3 libijs-0.35 libimobiledevice1 libindicate-gtk2 libindicate4
  libindicator1 libiptcdata0 libisc60 libisccc60 libisccfg60 libisofs6 libiw30
  libjack-jackd2-0 libjasper1 libjpeg62 libjson-glib-1.0-0 libk5crypto3
  libkate1 libkeyutils1 libkpathsea5 libkrb5-3 libkrb5support0
  liblaunchpad-integration1 liblaunchpad-integration1.0-cil liblcms1
  libldap-2.4-2 liblircclient0 liblocale-gettext-perl liblockfile1 liblouis2
  liblqr-1-0 libltdl7 liblua5.1-0 liblwres60 liblzma2 libmad0 libmagic1
  libmagickcore3 libmagickwand3 libmailtools-perl libmeanwhile1
  libmetacity-private0 libmimic0 libmission-control-plugins0 libmldbm-perl
  libmms0 libmng1 libmodplug1 libmono-addins-gui0.2-cil libmono-addins0.2-cil
  libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil
  libmono-management2.0-cil libmono-posix2.0-cil libmono-security2.0-cil
  libmono-sharpzip2.84-cil libmono-system2.0-cil libmpcdec6 libmpeg2-4
  libmpfr4 libmtdev1 libmtp8 libmusicbrainz4c2a libnautilus-extension1
  libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil
  libneon27-gnutls libnet-dbus-perl libnewt0.52 libnice0 libnih-dbus1 libnih1
  libnl1 libnm-glib2 libnm-util1 libnotify1 libnspr4-0d libnss-mdns libnss3-1d
  libntfs-3g79 libntfs10 libofa0 libogg0 liboil0.3 liboobs-1-5 libopencc1
  libopencore-amrnb0 libopencore-amrwb0 libopenobex1 libopenspc0 liborbit2
  liborc-0.4-0 libpam-ck-connector libpam-gnome-keyring libpam-modules
  libpam-runtime libpam0g libpanel-applet2-0 libpango-perl libpango1.0-0
  libpango1.0-common libpangomm-1.4-1 libpaper-utils libpaper1
  libparted0debian1 libpcap0.8 libpci3 libpciaccess0 libpcre3 libpcsclite1
  libperl5.10 libpixman-1-0 libplist1 libplymouth2 libpng12-0
  libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0
  libpolkit-gtk-1-0 libpoppler-glib5 libpoppler7 libpopt0 libportaudio2
  libpostproc51 libprotobuf6 libprotoc6 libproxy0 libpth20 libpulse-browse0
  libpulse-mainloop-glib0 libpulse0 libpurple-bin libpurple0 libpython2.6
  libqt4-dbus libqt4-network libqt4-xml libqtcore4 libqtgui4 libraptor1
  librarian0 librasqal2 libraw1394-11 librdf0 libreadline6 librpc-xml-perl
  librsvg2-2 librsvg2-common librtmp0 libsamplerate0 libsane libsane-hpaio
  libsasl2-2 libsasl2-modules libschroedinger-1.0-0 libsctp1 libsdl1.2debian
  libsdl1.2debian-pulseaudio libselinux1 libsensors4 libsepol1 libsgutils2-2
  libshout3 libsidplay1 libsigc++-2.0-0c2a libsilc-1.1-2 libsilcclient-1.1-3
  libslang2 libslp1 libsm6 libsmbclient libsndfile1 libsnmp15 libsoundtouch1c2
  libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1
  libspeexdsp1 libsqlite3-0 libss2 libssl0.9.8 libstartup-notification0
  libstdc++6 libstlport4.6ldbl libswscale0 libsyncdaemon-1.0-1 libsysfs2
  libt1-5 libtag1-vanilla libtag1c2a libtalloc2 libtasn1-3 libtdb1
  libtelepathy-farsight0 libtelepathy-glib0 libtelepathy-logger1
  libterm-readkey-perl libtext-charwidth-perl libtext-iconv-perl
  libtext-wrapi18n-perl libthai0 libtheora0 libtie-ixhash-perl libtiff4
  libtimedate-perl libtotem-plparser17 libts-0.0-0 libtwolame0
  libubuntuone-1.0-1 libudev0 libunique-1.0-0 libupower-glib1 liburi-perl
  libusb-0.1-4 libusb-1.0-0 libusbmuxd1 libutempter0 libutouch-grail1
  libuuid-perl libuuid1 libv4l-0 libva1 libvala-0.10-0 libvisual-0.4-0
  libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx0
  libvte9 libwavpack1 libwbclient0 libwebkit-1.0-2 libwildmidi0 libwmf0.2-7
  libwmf0.2-7-gtk libwnck22 libwpd8c2a libwpg-0.1-1 libwps-0.1-1 libwrap0
  libwww-perl libx11-6 libx11-xcb1 libx86-1 libxapian15 libxau6 libxaw7
  libxcb-atom1 libxcb-aux0 libxcb-dri2-0 libxcb-event1 libxcb-render0
  libxcb-shm0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6
  libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxkbfile1
  libxklavier16 libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxml2
  libxml2-utils libxmu6 libxmuu1 libxp6 libxpm4 libxrandr2 libxrender1
  libxres1 libxslt1.1 libxss1 libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1
  libxxf86vm1 libzbar0 libzephyr4 light-themes linux-generic
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
  linux-headers-generic linux-image-2.6.35-22-generic linux-image-generic
  linux-sound-base lksctp-tools lm-sensors locales lockfile-progs login
  logrotate lp-solve lsb-base lsb-release lshw lsof ltrace lzma make makedev
  man-db mawk media-player-info memtest86+ metacity metacity-common min12xxw
  mlocate modemmanager module-init-tools mono-2.0-gac mono-csharp-shell
  mono-gac mono-gmcs mono-runtime mount mountall mousetweaks mscompress mtools
  mtr-tiny myspell-en-au myspell-en-gb myspell-en-za nano nautilus
  nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share
  ncurses-bin net-tools netbase netcat-openbsd network-manager
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome
  notify-osd ntfs-3g ntfsprogs ntpdate nvidia-common obex-data-server
  obexd-client onboard openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-hyphenation
  openoffice.org-hyphenation-en-us openoffice.org-impress
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-style-human openoffice.org-thesaurus-en-au
  openoffice.org-thesaurus-en-us openoffice.org-writer openprinting-ppds
  openssh-client openssl os-prober parted passwd pciutils pcmciautils perl
  perl-base perl-modules pitivi pkg-config plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text pm-utils pnm2ppa
  policykit-1 policykit-1-gnome poppler-utils popularity-contest
  powermgmt-base ppp pppconfig pppoeconf pptp-linux procps protobuf-compiler
  psmisc pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr python
  python-appindicator python-apport python-apt python-aptdaemon
  python-aptdaemon-gtk python-argparse python-avahi python-brlapi python-cairo
  python-central python-configglue python-couchdb python-crypto python-cups
  python-cupshelpers python-dbus python-debian python-desktopcouch-records
  python-egenix-mxdatetime python-egenix-mxtools python-farsight python-gconf
  python-gdbm python-glade2 python-gmenu python-gnome2 python-gnomeapplet
  python-gnomecanvas python-gnomekeyring python-gnupginterface python-gobject
  python-gobject-cairo python-gst0.10 python-gtk2 python-gtksourceview2
  python-gtkspell python-httplib2 python-ibus python-imaging python-indicate
  python-launchpad-integration python-launchpadlib python-lazr.restfulclient
  python-lazr.uri python-libproxy python-libxml2 python-louis python-mako
  python-markupsafe python-minimal python-newt python-notify python-oauth
  python-openssl python-pam python-papyon python-pexpect python-pkg-resources
  python-problem-report python-protobuf python-pyatspi python-pycurl
  python-pygoocanvas python-pyinotify python-pyorbit python-rdflib
  python-serial python-simplejson python-smbc python-software-properties
  python-speechd python-support python-telepathy python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web python-ubuntuone
  python-ubuntuone-client python-ubuntuone-storageprotocol python-uno
  python-virtkey python-vte python-wadllib python-webkit python-wnck
  python-xapian python-xdg python-xkit python-zope.interface python2.6
  python2.6-minimal quadrapassel radeontool rarian-compat rdesktop
  readline-common rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store rsync rsyslog rtkit samba-common
  samba-common-bin sane-utils screen screen-resolution-extra
  screensaver-default-images seahorse sed sessioninstaller sgml-base sgml-data
  shared-mime-info shotwell simple-scan skype smbclient software-center
  software-properties-gtk speech-dispatcher splix ssh-askpass-gnome ssl-cert
  strace sudo synaptic syslinux system-config-printer-common
  system-config-printer-gnome system-config-printer-udev system-tools-backends
  sysv-rc sysvinit-utils tar tcl tcl8.4 tcpd tcpdump telepathy-butterfly
  telepathy-gabble telepathy-haze telepathy-idle telepathy-logger
  telepathy-mission-control-5 telepathy-salut telnet time tomboy toshset totem
  totem-common totem-mozilla totem-plugins transmission-gtk tsclient
  ttf-ubuntu-font-family ttf-unfonts-core tzdata tzdata-java ubufox
  ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-extras-keyring
  ubuntu-minimal ubuntu-mono ubuntu-sso-client ubuntu-standard
  ubuntu-system-service ubuntu-wallpapers ubuntuone-client
  ubuntuone-client-gnome ucf udev udisks ufw unattended-upgrades uno-libs3
  unzip update-inetd update-manager update-manager-core update-notifier
  update-notifier-common upower upstart ure ureadahead usb-creator-common
  usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd usbutils
  util-linux uuid-runtime vbetool vim-common vim-tiny vinagre vino w3m
  wamerican wbritish wget whiptail whois wireless-crda wireless-tools wodim
  wpasupplicant x-ttcidfont-conf x11-apps x11-common x11-session-utils
  x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xauth xdg-user-dirs
  xdg-user-dirs-gtk xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings
  xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xml-core xorg
  xscreensaver-data xscreensaver-gl xserver-common xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo xsltproc xterm xul-ext-ubufox xulrunner-1.9.2
  xz-utils yelp zenity zip zlib1g
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt) zlib1g
  (due to apt) base-files base-passwd (due to base-files) libpam-modules (due
  to base-files) mawk (due to base-files) bash debianutils (due to bash) dash
  (due to bash) libncurses5 (due to bash) bsdutils coreutils libacl1 (due to
  coreutils) libattr1 (due to coreutils) libselinux1 (due to coreutils) dpkg
  (due to dash) diffutils libbz2-1.0 (due to dpkg) xz-utils (due to dpkg)
  e2fsprogs e2fslibs (due to e2fsprogs) libblkid1 (due to e2fsprogs)
  libcomerr2 (due to e2fsprogs) libss2 (due to e2fsprogs) libuuid1 (due to
  e2fsprogs) util-linux (due to e2fsprogs) findutils grep install-info (due to
  grep) gzip hostname upstart (due to hostname) login libpam0g (due to login)
  libpam-runtime (due to login) mount libsepol1 (due to mount) ncurses-bin
  perl-base python-minimal python2.6-minimal (due to python-minimal) sed tar
  lsb-base (due to util-linux) tzdata (due to util-linux) libslang2 (due to
  util-linux)
0 upgraded, 0 newly installed, 1267 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,135MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'


shall i say yes?

---

### Post by sikander3786 on 2010-10-19
> shall i say yes?

No.

Seems like you need a partial upgrade.

Please wait a bit.

Edit: You said Ubuntu 10. Which one is it exactly, 10.04 or 10.10?

---

### Post by sikander3786 on 2010-10-19
Disable any third party ppa's from System > Administration > Software Sources.

Now,

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

And still if broken packages persist, again

```
sudo apt-get install -f
```

Can you fix them now?

---

### Post by kekearif on 2010-10-19
> **sikander3786 said:**
> Disable any third party ppa's from System > Administration > Software Sources.

Now,

```
sudo dpkg --configure -a
``````
sudo apt-get update
``````
sudo apt-get upgrade
```And still if broken packages persist, again

```
sudo apt-get install -f
```Can you fix them now?

keke@keke-R510-P510:~$ sudo dpkg --configure -a
[sudo] password for keke: 
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.12.1-0ubuntu7); however:
  Version of libc6 on system is 2.12.1-0ubuntu6.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
keke@keke-R510-P510:~$ sudo apt-get update
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick Release.gpg
Ign [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick Release                            
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick-updates Release                      
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick/multiverse Sources                 
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick/restricted i386 Packages           
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick-updates/multiverse Sources         
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick-updates/restricted i386 Packages   
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
84% [Connecting to security.ubuntu.com (91.189.92.167)]sudo apt-get upgrade
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
keke@keke-R510-P510:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.12.1-0ubuntu6) but 2.12.1-0ubuntu7 is installed
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu7) but 2.12.1-0ubuntu6 is installed
E: Unmet dependencies. Try using -f.


that's what I get... no luck

---

### Post by sikander3786 on 2010-10-19
The command

```
sudo apt-get update
```

itself was not successful. Try changing the update server from System > Administration > Software Sources, select the Main server and try again.

---

### Post by directhex on 2010-10-19
Somehow you've got your libc6, libc6-bin and libc6-dev package versions out of whack.

"apt-cache policy packagename" will tell you which version of packagename you have installed, and which is on the repositories

Also, try this:

apt-get install libc6=2.12.1-0ubuntu6 libc6-dev=2.12.1-0ubuntu6

---

### Post by tusk on 2010-10-19
Just downloaded and installed 10.10 had the same problem

---

### Post by Debatablor on 2010-10-20
Same hare, have a Evo-N610c Compaq laptop.

my name is Mr.Bla - respect (fictional name)

bla@bla bla:~$ **sudo apt-get update**
[sudo] password for bla: bla blaBla11!!1!!
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick Release.gpg
Ign [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick Release                              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick/main Sources                         
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick/restricted Sources         
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick/universe Sources                     
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick/multiverse Sources                   
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick/main i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick/restricted i386 Packages             
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick/universe i386 Packages     
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) maverick/multiverse i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Reading package lists... Done

bla@bla bla:~$ **sudo apt-get check**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.12.1-0ubuntu6) but 2.12.1-0ubuntu7 is installed
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu7) but 2.12.1-0ubuntu6 is installed
E: Unmet dependencies. Try using -f.

bla@bla bla:~$ **sudo apt-get -f**
apt 0.8.3ubuntu7 for i386 compiled on Oct  5 2010 14:07:36
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

bla@ble bla:~$ [B]apt-cache policy libc6 libc6-dev
[/B]libc6:
  Installed: 2.12.1-0ubuntu6
  Candidate: 2.12.1-0ubuntu6
  Version table:
 *** 2.12.1-0ubuntu6 0
        500 [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick/main i386 Packages
        100 /var/lib/dpkg/status
libc6-dev:
  Installed: 2.12.1-0ubuntu7
  Candidate: 2.12.1-0ubuntu7
  Version table:
 *** 2.12.1-0ubuntu7 0
        100 /var/lib/dpkg/status
     2.12.1-0ubuntu6 0
        500 [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick/main i386 Packages

bla@bla bla:~$ **sudo apt-get install libc6-dev=2.12.1-0ubuntu6**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.12.1-0ubuntu6) but 2.12.1-0ubuntu7 is to be installed
 libc6-dev : Depends: libc-dev-bin (= 2.12.1-0ubuntu6) but 2.12.1-0ubuntu7 is to be installed

bla@bla bla:~$ **sudo apt-get install libc-bin=2.12.1-0ubuntu6 libc-dev-bin=2.12.1-0ubuntu6**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu7) but 2.12.1-0ubuntu6 is to be installed
             Depends: libc-dev-bin (= 2.12.1-0ubuntu7) but 2.12.1-0ubuntu6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

bla@bla bla:~$ **sudo apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.12.1-0ubuntu6) but 2.12.1-0ubuntu7 is installed
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu7) but 2.12.1-0ubuntu6 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

bla@bla bla:~$ **sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.12.1-0ubuntu6) but 2.12.1-0ubuntu7 is installed
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu7) but 2.12.1-0ubuntu6 is installed
E: Unmet dependencies. Try using -f.

edit- maybe force version ?

i thought to simply reformat the system, i have reformatted my Ubuntu live flesh drive to a new maverick copy. if you can't find any thing else one can do...  thanks in advance.

---

### Post by Debatablor on 2010-10-20
BTW, i am new hare and would like to know what to do next, please. And how can i jump foreword the subject in order o make sure it is attended? 

thank you in advance

---

### Post by Hippytaff on 2010-10-20
did you try 

```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by Debatablor on 2010-10-20
> **Hippytaff said:**
> did you try 

```

sudo apt-get update && sudo apt-get upgrade

```
I did, it's the version... should i reformat?

---

### Post by Hippytaff on 2010-10-20
sounds to me like a broken install...check to see if you can boot from live cd. if it works you can do a fresh install, if your happy to, or maybe download the 10.04 iso and try booting that and installing it if the cd works :-)

---

### Post by directhex on 2010-10-20
> **Debatablor said:**
> 
bla@bla bla:~$ **sudo apt-get install libc6-dev=2.12.1-0ubuntu6**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.12.1-0ubuntu6) but 2.12.1-0ubuntu7 is to be installed
 libc6-dev : Depends: libc-dev-bin (= 2.12.1-0ubuntu6) but 2.12.1-0ubuntu7 is to be installed

"apt-get install libc-bin=2.12.1-0ubuntu6 libc-dev-bin=2.12.1-0ubuntu6"

---

### Post by Hippytaff on 2010-10-20
> **directhex said:**
> "apt-get install libc-bin=2.12.1-0ubuntu6 libc-dev-bin=2.12.1-0ubuntu6"

+1 this

do this first before you start over...thought you had already tried it to no avail :-)

---

### Post by Debatablor on 2010-10-20
> **directhex said:**
> "apt-get install libc-bin=2.12.1-0ubuntu6 libc-dev-bin=2.12.1-0ubuntu6"
Done-

bla@bla bla:~$ **sudo apt-get install libc-bin=2.12.1-0ubuntu6 libc-dev-bin=2.12.1-0ubuntu6**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu7) but 2.12.1-0ubuntu6 is to be installed
             Depends: libc-dev-bin (= 2.12.1-0ubuntu7) but 2.12.1-0ubuntu6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

(i add it to my original message for ease of use)

Well, if i was the only one with the problem... but i ain't, so the problem must be solved for others as well. And i learn a thing or two in the process.

---

### Post by Hippytaff on 2010-10-20
I don't know about you, but if your not going to loose any important data, and your not too bothered about trying to fix this for the fun of it, then I'd go for a fresh install :-)

---

### Post by mc4man on 2010-10-20
could you open software sources (not in menu by default anymore - open Applications -> Ubuntu Software Center -> edit - Software Sources.

Under the updates tab make sure that the first 2 are checked - Maverick-security and Maverick-updates
If you had to ck one then click close and reload and try again.

If both are checked then go under the Ubuntu Software tab and switch to the main server, close and reload, ect.

---

### Post by Debatablor on 2010-10-20
> **mc4man said:**
> could you open software sources (not in menu by default anymore - open Applications -> Ubuntu Software Center -> edit - Software Sources.

Under the updates tab make sure that the first 2 are checked - Maverick-security and Maverick-updates
If you had to ck one then click close and reload and try again.

If both are checked then go under the Ubuntu Software tab and switch to the main server, close and reload, ect.
wow, done! thank you.

i guess Israel server doesn't fully support maverick just yet

BTW
 open system -> administration -> synaptic package manager -> settings -> repositories -> Software Sources

synaptic package manager -> edit -> fix broken packages

thank you and good night.

---

### Post by Hippytaff on 2010-10-20
phew...impressive :-) could have done with you about 20 posts ago :-D

---

### Post by directhex on 2010-10-21
> **Debatablor said:**
> Done-

bla@bla bla:~$ **sudo apt-get install libc-bin=2.12.1-0ubuntu6 libc-dev-bin=2.12.1-0ubuntu6**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu7) but 2.12.1-0ubuntu6 is to be installed
             Depends: libc-dev-bin (= 2.12.1-0ubuntu7) but 2.12.1-0ubuntu6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

(i add it to my original message for ease of use)

Well, if i was the only one with the problem... but i ain't, so the problem must be solved for others as well. And i learn a thing or two in the process.

Remove libc6-dev

---

### Post by kekearif on 2010-10-21
hey guys I fixed it.... turn off the 3rd party repository then run the commands stated previously..

---

### Post by Hippytaff on 2010-10-21
Excellent - Remember to mark the thread as solved in the forum tools at the top of the page, so others don't have to work as hard as you have to resolve it :-)

---

