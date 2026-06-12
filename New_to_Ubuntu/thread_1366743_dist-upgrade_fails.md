---
title: "dist-upgrade fails"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Zopiac on 2009-12-28
Trying to dist-upgrade from 9.04:

```

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  compiz-gnome: Depends: libmetacity-private0 (>= 1:2.26.0) but it is not installed
  cupsddk: Depends: cups-ppdc but it is not installed
  gdm: Depends: libdevkit-power-gobject1 (>= 010) but it is not installed
       Depends: gnome-session-bin but it is not installed
  gnome-control-center: Depends: libmetacity-private0 (>= 1:2.26.0) but it is not installed
  gnome-session: Depends: gnome-session-bin (>= 2.28) but it is not installed
                 Depends: gnome-session-bin (< 2.29) but it is not installed
  python-metacity: Depends: libmetacity-private0 (>= 1:2.26.0) but it is not installed
  ubuntu-desktop: Depends: indicator-applet-session but it is not installed
                  Depends: libgd2-xpm but it is not installed
                  Depends: software-center but it is not installed
                  Depends: xsplash but it is not installed
                  Recommends: aisleriot but it is not installed
                  Recommends: brasero but it is not installed
                  Recommends: evolution-couchdb but it is not installed
                  Recommends: firefox
                  Recommends: firefox-gnome-support but it is not installed
                  Recommends: gnome-bluetooth but it is not installed
                  Recommends: gnome-disk-utility but it is not installed
                  Recommends: gnome-mahjongg but it is not installed
                  Recommends: gnome-sudoku
                  Recommends: gnomine but it is not installed
                  Recommends: ibus but it is not installed
                  Recommends: ibus-gtk but it is not installed
                  Recommends: ibus-m17n but it is not installed
                  Recommends: ibus-table but it is not installed
                  Recommends: kerneloops-daemon but it is not installed
                  Recommends: openoffice.org-gnome but it is not installed
                  Recommends: openoffice.org-help-en-us but it is not installed
                  Recommends: pm-utils-powersave-policy but it is not installed
                  Recommends: pulseaudio-module-bluetooth but it is not installed
                  Recommends: quadrapassel but it is not installed
                  Recommends: speech-dispatcher but it is not installed
                  Recommends: telepathy-idle but it is not installed
                  Recommends: ttf-kacst but it is not installed
                  Recommends: ttf-vlgothic but it is not installed
                  Recommends: ubufox but it is not installed
                  Recommends: ubuntuone-client-gnome but it is not installed
                  Recommends: usb-creator-gtk but it is not installed
E: Unmet dependencies. Try using -f.
``````

$ sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  empathy evolution-documentation-en libart2.24-cil libcv1 libempathy-gtk19
  libempathy23 libgconf2.24-cil libgd2-noxpm libgdl-1-0 libgnome-vfs2.24-cil
  libhighgui1 libmbca0 libmetacity0 librpm4.4 libsox1 linux-rt miro
  mono-2.0-runtime mono-common mono-jit plib1.8.4c2 python-gnome2-extras
The following NEW packages will be installed:
  a2jmidid akonadi-server apport-symptoms aptdaemon apturl-common
  bcmwl-modaliases bristol-data byobu conky-all cpp-4.4 cups-ppdc
  devicekit-disks devicekit-power diffutils frei0r-plugins g++-4.4 gcc-4.4
  geoip-database gnome-session-bin hplip-cups humanity-icon-theme
  indicator-applet-session indicator-session insserv jackd-firewire
  kcm-phonon-xine kdebase-runtime kdebase-runtime-data kdebase-workspace-bin
  kdebase-workspace-data kdebase-workspace-kgreet-plugins kdelibs-bin kdelibs5
  kdelibs5-data kdepim-runtime kdepimlibs-data kdepimlibs5 ksysguardd
  libaccess-bridge-java-jni libakonadiprivate1 libamrnb3 libamrwb3 libanthy0
  libappindicator0-cil libart2.0-cil libass4 libatasmart4 libattica0
  libaudclient2 libaudcore1 libaudid3tag2 libaudutil1 libavahi-core6
  libbind9-50 libboost-date-time1.38.0 libboost-filesystem1.40.0
  libboost-program-options1.40.0 libboost-python1.38.0 libboost-python1.40.0
  libboost-system1.40.0 libboost-thread1.38.0 libboost-thread1.40.0 libbsd0
  libclucene0ldbl libcompress-raw-bzip2-perl libcorosync4 libcsound64-5.2
  libcv4 libcvaux4 libdevkit-power-gobject1 libdirac0c2a libdns53
  libdotconf1.0 libdrm-radeon1 libdvbpsi5 libevent-1.4-2 libexo-common
  libfaad2 libffado1 libflickrnet2.2-cil libgavl1 libgconf2.0-cil libgd2-xpm
  libgdata-common libgdata6 libgeoip1 libgme0 libgnome-bluetooth7
  libgnome-vfs2.0-cil libgssdp-1.0-1 libgssdp-1.0-2 libgupnp-1.0-2
  libgupnp-igd-1.0-2 libhighgui4 libindicate-gtk1 libindicate3
  libio-compress-perl libiodbc2 libisc50 libisccc50 libisccfg50 libiso9660-7
  libjline-java libjs-jquery libk3b6 libkate1 libkcddb4 libkephal4
  libkfontinst4 libkscreensaver5 libksgrd4 libkworkspace4 liblouis-data
  liblouis0 liblwres50 liblzma1 libm17n-0 libmagick++2 libmagickcore2
  libmagickcore2-extra libmagickwand2 libmetacity-private0 libmimic0
  libmono-i18n-west2.0-cil libnm-glib2 libntfs-3g54 libopal3.6.4 libopenais3
  libopencore-amrnb0 libopencore-amrwb0 libopenjpeg2 libopenraw1
  libopenrawgnome1 libotf0 libpango-perl libpano13-1 libparted1.8-12
  libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma3
  libplasmaclock4 libplib1 libpolkit-gtk-1-0 libpolkit-qt-1-0 libpolkit-qt0
  libprocesscore4 libprocessui4 libprojectm-data libprojectm2 libpst4
  libpt2.6.4 libqca2 libqimageblitz4 libqt4-phonon librpm0 librpmbuild0
  librpmio0 libsad2 libsensors4 libsgutils2-2 libsilcclient-1.1-3
  libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libsox-fmt-pulse
  libsox1a libspeechd2 libstdc++6-4.4-dev libstreamanalyzer0 libstreams0
  libsub-name-perl libsubtitleeditor0 libtaskmanager4 libtiff-tools
  libtorrent-rasterbar5 libupnp3 libvlccore2 libweather-ion4 libwebkit-1.0-2
  libwebkit-1.0-common libweed0 libx264-67 libxcb-keysyms1 libzephyr4
  linux-headers-2.6.31-9-rt linux-headers-2.6.32-9
  linux-headers-2.6.32-9-generic linux-image-2.6.31-9-rt
  linux-image-2.6.32-9-generic linux-rt-headers-2.6.31-9 lives-data lm-sensors
  m17n-contrib m17n-db modemmanager mysql-server-core-5.1
  nvidia-185-modaliases odbcinst oxygen-icon-theme phonon phonon-backend-xine
  plasma-dataengines-workspace plasma-widgets-workspace polkit-kde-1
  python-aptdaemon python-aptdaemon-gtk python-httplib2 python-kde4
  python-launchpadlib python-lazr.restfulclient python-lazr.uri python-louis
  python-oauth python-papyon python-pexpect python-simplejson python-speechd
  python-wadllib python-webkit rakarrack rpm-common rpm2cpio samba-common-bin
  software-center soprano-daemon speech-dispatcher subtitleeditor
  system-config-printer-udev trigger-rally trigger-rally-data tuxguitar-jsa
  ubuntu-xsplash-artwork usb-creator-common usb-creator-gtk vlc-plugin-pulse
  xfce-keyboard-shortcuts xorg-docs-core xsplash xulrunner-1.9.1 xwax
The following packages have been kept back:
  ekiga gstreamer0.10-plugins-bad ubuntustudio-video
The following packages will be upgraded:
  acpid apport apturl at audacious audacious-plugins audacious-plugins-extra
  audacity audacity-data avahi-daemon bind9-host blender bristol cheese compiz
  compizconfig-backend-gconf computer-janitor computer-janitor-gtk conky cpp
  cron csound csound-gui csound-utils diff dnsutils evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-exchange
  evolution-indicator evolution-plugins exo-utils f-spot ffado-dbus-server
  ffado-mixer-qt4 ffado-tools fontmatrix ftp g++ gcc gdb gdm-guest-session
  gimp gimp-data gimp-plugin-registry gksu gnash gnash-common gnome-do
  gnome-do-docklets gnome-do-plugins gnome-mag gnome-network-admin gnome-orca
  gnome-panel gnome-panel-data gnome-power-manager gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-themes-ubuntu gnupg-agent gnupg2
  gparted gpsd-clients grub gstreamer0.10-plugins-ugly gthumb gthumb-data
  guile-1.8-libs hal hal-cups-utils hostname hpijs hplip hplip-data hugin
  hugin-data hugin-tools human-theme icedtea-6-jre-cacao imagemagick
  indicator-messages info initscripts inkscape jack-tools jackbeat jackd
  jockey-common jockey-gtk k3b k3b-data kdelibs-data lat lftp libawn0
  libclass-accessor-perl libcompress-raw-zlib-perl libcompress-zlib-perl
  libcorosync-dev libedataserverui1.2-8 libedit2 libempathy-common
  libempathy-gtk-common libexo-0.3-0 libgdata1.4-cil libgdl-1-common
  libgimp2.0 libgksu2-0 libgl1-mesa-dri libgl1-mesa-glx libgnome2.24-cil
  libgnomedesktop2.20-cil libgpod-common libgstfarsight0.10-0 libgtk2-perl
  libio-compress-base-perl libio-compress-zlib-perl libjack0 libjack0.100.0-0
  libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-corlib2.0-cil
  libmono-data-tds2.0-cil libmono-data2.0-cil libmono-getoptions2.0-cil
  libmono-i18n2.0-cil libmono-ldap2.0-cil libmono-posix2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil
  libmono2.0-cil libndesk-dbus1.0-cil libnice0 libopenais-dev libpam-smbpass
  libpano13-bin libpstoedit0c2a libpurple0 libsdl1.2debian libsdl1.2debian-all
  libsnmp15 libsoqt-dev-common libsoqt4-20 libsox-fmt-all libsox-fmt-alsa
  libsox-fmt-ao libsox-fmt-base libsox-fmt-ffmpeg libsox-fmt-mp3
  libsox-fmt-oss libvlc2 libxfcegui4-4 libxine1 libxine1-bin libxine1-console
  libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x
  libxml2-utils linux-generic linux-headers-generic linux-headers-rt
  linux-image-generic linux-image-rt lives mencoder metacity metacity-common
  mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mplayer
  network-manager network-manager-gnome nfs-common ntfs-3g
  nvidia-180-modaliases nvidia-common obex-data-server odbcinst1debian1
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib parted perlmagick
  pidgin pidgin-data pidgin-libnotify pidgin-otr portmap python-apport
  python-awn python-gtkhtml2 python-libtorrent python-opencv rhino rpm rss-glx
  samba samba-common screen-profiles screen-resolution-extra sg3-utils
  smbclient sox splix system-tools-backends sysv-rc telepathy-butterfly
  telepathy-haze texlive-base-bin texlive-base-bin-doc tomboy torcs totem
  totem-common totem-gstreamer totem-mozilla totem-plugins transmission
  transmission-cli transmission-common transmission-daemon transmission-gtk
  trigger tuxguitar tuxguitar-alsa tuxguitar-oss ubuntu-system-service
  ubuntustudio-audio ufw unixodbc update-notifier usb-creator vlc vlc-nox
  winbind wpasupplicant xfce4-panel xorg xscreensaver-data
  xserver-xorg-video-ati yelp
253 upgraded, 240 newly installed, 22 to remove and 3 not upgraded.
158 not fully installed or removed.
Need to get 0B/488MB of archives.
After this operation, 917MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 249374 files and directories currently installed.)
Preparing to replace metacity 1:2.25.144-0ubuntu2 (using .../metacity_1%3a2.28.0-2ubuntu1_i386.deb) ...
Unpacking replacement metacity ...
dpkg: error processing /var/cache/apt/archives/metacity_1%3a2.28.0-2ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/share/applications/metacity.desktop', which is also in package metacity-common 1:2.25.144-0ubuntu2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF-8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/metacity_1%3a2.28.0-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any clue as to what the problem and solution is?

---

### Post by yeats on 2009-12-28
```
**You might want to run `apt-get -f install' to correct these.**

```

Have you tried ```
sudo apt-get -f install
```?

---

### Post by Zopiac on 2009-12-28
> **chrissharp123 said:**
> ```
**You might want to run `apt-get -f install' to correct these.**

```

Have you tried ```
sudo apt-get -f install
```?

Yeah I have, but forgot to post it.

```

$ sudo apt-get -f install
[sudo] password for zopiac: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  qt4-doc libcaca-dev libaudiofile-dev libaudio-dev nvidia-settings libgps17
  libxmu-headers gpsd-clients qt4-designer libxp-dev libqt4-dev qt4-dev-tools
  qt4-qmake libxt-dev libxmu-dev lesstif2 libtiff4-dev libesd0-dev libxpm-dev
  x11proto-print-dev libasound2-dev libqt4-multimedia libtiffxx0c2
  libsoqt-dev-common libslang2-dev libncurses5-dev libaa1-dev
  nvidia-180-libvdpau
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptdaemon cups-ppdc devicekit-power gnome-power-manager gnome-session-bin
  indicator-applet-session indicator-session libdevkit-power-gobject1
  libgd2-xpm libmetacity-private0 libwebkit-1.0-2 libwebkit-1.0-common
  metacity metacity-common python-aptdaemon python-aptdaemon-gtk python-webkit
  software-center ubuntu-xsplash-artwork xsplash
Suggested packages:
  libgd-tools
The following packages will be REMOVED:
  libgd2-noxpm libmetacity0
The following NEW packages will be installed:
  aptdaemon cups-ppdc devicekit-power gnome-session-bin
  indicator-applet-session indicator-session libdevkit-power-gobject1
  libgd2-xpm libmetacity-private0 libwebkit-1.0-2 libwebkit-1.0-common
  python-aptdaemon python-aptdaemon-gtk python-webkit software-center
  ubuntu-xsplash-artwork xsplash
The following packages will be upgraded:
  gnome-power-manager metacity metacity-common
3 upgraded, 17 newly installed, 2 to remove and 256 not upgraded.
158 not fully installed or removed.
Need to get 0B/8,573kB of archives.
After this operation, 19.9MB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 249374 files and directories currently installed.)
Preparing to replace metacity 1:2.25.144-0ubuntu2 (using .../metacity_1%3a2.28.0-2ubuntu1_i386.deb) ...
Unpacking replacement metacity ...
dpkg: error processing /var/cache/apt/archives/metacity_1%3a2.28.0-2ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/share/applications/metacity.desktop', which is also in package metacity-common 1:2.25.144-0ubuntu2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF-8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/metacity_1%3a2.28.0-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Zopiac on 2009-12-28
My computer (Ubuntu-wise) is pretty much useless until I get this fixed. The first time I ran dist-upgrade it got as far to remove all of my sound stuff to install new versions of them, so I can't even listen to music or anything :(

---

