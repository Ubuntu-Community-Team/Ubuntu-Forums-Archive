---
title: "Issues with 10.04 to 10.10"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by rawrxiv on 2011-01-18
Good day,

I was looking to upgrade to 10.10 today through the network upgrade tool and got stopped up on:


> An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
I was wondering if anyone would be able to help me to figure out which package is stopping me up.

follows are the logs from the upgrade:

**Main.log**
```
2011-01-18 18:27:25,900 INFO Using config files '['./DistUpgrade.cfg']'
2011-01-18 18:27:25,900 INFO uname information: 'Linux ubuntu 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64'
2011-01-18 18:27:25,901 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/preferences.d/', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2011-01-18 18:27:26,049 INFO release-upgrader version '0.142.20' started
2011-01-18 18:27:26,205 DEBUG svg pixbuf loader failed (Error displaying image)
2011-01-18 18:27:26,254 DEBUG Using 'DistUpgradeViewGtk' view
2011-01-18 18:27:26,320 DEBUG aufsOptionsAndEnvironmentSetup()
2011-01-18 18:27:26,321 DEBUG using '/tmp/upgrade-rw-AG4nDm' as aufs_rw_dir
2011-01-18 18:27:26,321 DEBUG using '/tmp/upgrade-chroot-pWLLfQ' as aufs chroot dir
2011-01-18 18:27:26,321 DEBUG enable dpkg --force-overwrite
2011-01-18 18:27:26,374 DEBUG lsb-release: 'lucid'
2011-01-18 18:27:26,381 DEBUG who -m --ips: ''
2011-01-18 18:27:26,383 DEBUG _pythonSymlinkCheck run
2011-01-18 18:27:26,384 DEBUG openCache()
2011-01-18 18:27:26,689 DEBUG /openCache(), new cache size 30285
2011-01-18 18:27:26,690 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-01-18 18:27:26,690 DEBUG checkViewDepends()
2011-01-18 18:27:26,691 DEBUG running doUpdate() (showErrors=False)
2011-01-18 18:27:28,167 DEBUG openCache()
2011-01-18 18:27:28,542 DEBUG /openCache(), new cache size 30285
2011-01-18 18:27:28,542 DEBUG doPostInitialUpdate
2011-01-18 18:27:28,543 DEBUG Plugin modules in ./plugins: dpkg_status_plugin.py remove_lilo_plugin.py deb_plugin.py kdelibs4to5_plugin.py langpack_manual_plugin.py
2011-01-18 18:27:28,543 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2011-01-18 18:27:28,544 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2011-01-18 18:27:28,544 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2011-01-18 18:27:28,545 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2011-01-18 18:27:28,545 DEBUG Loading module ./plugins/deb_plugin.py
2011-01-18 18:27:28,545 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2011-01-18 18:27:28,545 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2011-01-18 18:27:28,546 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2011-01-18 18:27:28,546 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2011-01-18 18:27:28,547 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2011-01-18 18:27:28,547 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2011-01-18 18:27:28,547 DEBUG plugins for condition 'maverickPostInitialUpdate' are '[]'
2011-01-18 18:27:28,547 DEBUG plugins for condition 'from_lucidPostInitialUpdate' are '[]'
2011-01-18 18:27:30,561 DEBUG Foreign: xserver-xorg-video-intel xserver-xorg-video-ati nvidia-current nvidia-173-modaliases nvidia-current-modaliases google-chrome-stable nvidia-96-modaliases xserver-xorg-video-radeon flashplugin64-installer fglrx-modaliases nvidia-glx-185 nvidia-settings nvidia-173 intel-gpu-tools gstreamer0.10-fluendo-plugins-mp3-partner
2011-01-18 18:27:30,561 DEBUG Obsolete: 
2011-01-18 18:27:30,562 DEBUG updateSourcesList()
2011-01-18 18:27:30,601 DEBUG rewriteSourcesList()
2011-01-18 18:27:30,602 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted'
2011-01-18 18:27:30,602 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted' updated to new dist
2011-01-18 18:27:30,603 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted'
2011-01-18 18:27:30,603 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted' updated to new dist
2011-01-18 18:27:30,603 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted'
2011-01-18 18:27:30,603 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted' updated to new dist
2011-01-18 18:27:30,603 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted'
2011-01-18 18:27:30,603 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted' updated to new dist
2011-01-18 18:27:30,603 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ lucid universe'
2011-01-18 18:27:30,603 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ maverick universe' updated to new dist
2011-01-18 18:27:30,603 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe'
2011-01-18 18:27:30,603 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe' updated to new dist
2011-01-18 18:27:30,603 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe'
2011-01-18 18:27:30,603 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe' updated to new dist
2011-01-18 18:27:30,603 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe'
2011-01-18 18:27:30,603 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe' updated to new dist
2011-01-18 18:27:30,604 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse'
2011-01-18 18:27:30,604 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse' updated to new dist
2011-01-18 18:27:30,604 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse'
2011-01-18 18:27:30,604 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse' updated to new dist
2011-01-18 18:27:30,604 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse'
2011-01-18 18:27:30,604 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse' updated to new dist
2011-01-18 18:27:30,604 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse'
2011-01-18 18:27:30,604 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse' updated to new dist
2011-01-18 18:27:30,604 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security main restricted'
2011-01-18 18:27:30,604 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security main restricted' updated to new dist
2011-01-18 18:27:30,604 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted'
2011-01-18 18:27:30,604 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted' updated to new dist
2011-01-18 18:27:30,604 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security universe'
2011-01-18 18:27:30,604 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security universe' updated to new dist
2011-01-18 18:27:30,604 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security universe'
2011-01-18 18:27:30,604 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security universe' updated to new dist
2011-01-18 18:27:30,605 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security multiverse'
2011-01-18 18:27:30,605 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security multiverse' updated to new dist
2011-01-18 18:27:30,605 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse'
2011-01-18 18:27:30,605 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse' updated to new dist
2011-01-18 18:27:30,605 DEBUG examining: 'deb http://archive.canonical.com/ lucid partner'
2011-01-18 18:27:30,605 DEBUG entry 'deb http://archive.canonical.com/ maverick partner' updated to new dist
2011-01-18 18:27:30,605 DEBUG examining: 'deb http://archive.canonical.com/ubuntu lucid partner'
2011-01-18 18:27:30,605 DEBUG entry 'deb http://archive.canonical.com/ubuntu maverick partner' updated to new dist
2011-01-18 18:27:30,605 DEBUG examining: 'deb http://dl.google.com/linux/chrome/deb/ stable main'
2011-01-18 18:27:30,608 DEBUG entry '# deb http://dl.google.com/linux/chrome/deb/ stable main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-18 18:27:30,608 DEBUG examining: 'deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu lucid main'
2011-01-18 18:27:30,610 DEBUG entry '# deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-18 18:27:30,610 DEBUG examining: 'deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu lucid main'
2011-01-18 18:27:30,613 DEBUG entry '# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-18 18:27:36,569 DEBUG running doUpdate() (showErrors=True)
2011-01-18 18:29:34,915 DEBUG openCache()
2011-01-18 18:29:34,916 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-01-18 18:29:36,518 DEBUG /openCache(), new cache size 32193
2011-01-18 18:29:36,519 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-01-18 18:34:25,527 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2011-01-18 18:34:25,528 DEBUG abort called
2011-01-18 18:34:25,531 DEBUG openCache()
2011-01-18 18:34:25,532 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-01-18 18:34:27,046 DEBUG /openCache(), new cache size 30285
2011-01-18 18:34:27,047 DEBUG enabling apt cron job
```and 

**apt.log**
```
Log time: 2011-01-18 18:27:26.666846
Log time: 2011-01-18 18:27:28.538670
Log time: 2011-01-18 18:29:36.506407
  Installing libmono-corlib2.0-cil as Depends of libmono-data-tds2.0-cil
    Installing mono-runtime as Depends of libmono-corlib2.0-cil
      Installing mono-gac as Depends of mono-runtime
        Installing mono-2.0-gac as Depends of mono-gac
          Installing libc6 as Depends of mono-2.0-gac
            Installing libc-bin as Depends of libc6
          Installing libmono-security2.0-cil as Depends of mono-2.0-gac
            Installing libmono-system2.0-cil as Depends of libmono-security2.0-cil
  Installing libcairo2 as Depends of f-spot
    Installing libpixman-1-0 as Depends of libcairo2
    Installing libxcb-shm0 as Depends of libcairo2
  Installing libgdk-pixbuf2.0-0 as Depends of f-spot
    Installing libglib2.0-0 as Depends of libgdk-pixbuf2.0-0
      new important dependency: libdconf0
      Installing libdconf0 as Recommends of libglib2.0-0
  Installing libgtk2.0-0 as Depends of f-spot
  Installing gconf2 as Depends of f-spot
    Installing libgconf2-4 as Depends of gconf2
      Installing gconf2-common as Depends of libgconf2-4
  Installing libglib2.0-cil as Depends of f-spot
  Installing libgtk2.0-cil as Depends of f-spot
  Installing libmono-simd2.0-cil as Depends of f-spot
  Installing libmono-system-data2.0-cil as Depends of f-spot
    Installing libmono-wcf3.0-cil as Depends of libmono-system-data2.0-cil
      Installing libmono-system-messaging2.0-cil as Depends of libmono-wcf3.0-cil
        Installing libmono-messaging2.0-cil as Depends of libmono-system-messaging2.0-cil
  Installing libsqlite3-0 as Depends of f-spot
  Installing openoffice.org-core as Depends of openoffice.org-draw
    Installing openoffice.org-common as Depends of openoffice.org-core
    Installing libhunspell-1.2-0 as Depends of openoffice.org-core
    Installing libneon27-gnutls as Depends of openoffice.org-core
    Installing libssl0.9.8 as Depends of openoffice.org-core
    Installing libstdc++6 as Depends of openoffice.org-core
      Installing gcc-4.5-base as Depends of libstdc++6
    Installing ure as Depends of openoffice.org-core
      Installing uno-libs3 as Depends of ure
  Installing libglew1.5 as Depends of mesa-utils
  Installing libkrb5support0 as Depends of libkrb5-3
  Installing libpopt0 as Depends of python-gnome2
  Installing python-gconf as Depends of python-gnome2
  Installing perl as Depends of libpurple0
    Installing perl-base as Depends of perl
    Installing perl-modules as Depends of perl
  Installing syslinux-common as Depends of syslinux
    Installing libcrypt-passwdmd5-perl as Recommends of syslinux-common
    Installing libdigest-sha1-perl as Recommends of syslinux-common
  Installing apt as Depends of apt-transport-https
    new important dependency: gpg
  Installing foomatic-db-compressed-ppds as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing xz-utils as Depends of foomatic-db-compressed-ppds
      Installing liblzma2 as Depends of xz-utils
  Installing ubuntu-extras-keyring as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: ibus-pinyin
  Installing ibus-pinyin as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing ibus-pinyin-db-open-phrase as Depends of ibus-pinyin
      Installing pinyin-database as Depends of ibus-pinyin-db-open-phrase
    Installing libibus2 as Depends of ibus-pinyin
    Installing liblua5.1-0 as Depends of ibus-pinyin
    Installing libopencc1 as Depends of ibus-pinyin
    Installing ibus as Depends of ibus-pinyin
      Installing python-ibus as Depends of ibus
  new important dependency: ibus-pinyin-db-android
  Installing ibus-pinyin-db-android as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: shotwell
  Installing shotwell as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libexiv2-6 as Depends of shotwell
      Installing exiv2 as Recommends of libexiv2-6
    Installing libgee2 as Depends of shotwell
    Installing libgexiv2-0 as Depends of shotwell
  new important dependency: ttf-ubuntu-font-family
  Installing ttf-ubuntu-font-family as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  Installing libappindicator1 as Depends of gnome-power-manager
    Installing libdbus-glib-1-2 as Depends of libappindicator1
    Installing libdbusmenu-glib1 as Depends of libappindicator1
    Installing libdbusmenu-gtk1 as Depends of libappindicator1
    Installing libindicator1 as Depends of libappindicator1
    Installing indicator-application as Recommends of libappindicator1
  Installing libnotify1 as Depends of gnome-power-manager
  Installing libavutil50 as Depends of libswscale0
  Installing libappindicator0.1-cil as Depends of tomboy
  Installing libbz2-1.0 as Depends of bzip2
  Installing libespeak1 as Depends of espeak
    Installing libportaudio2 as Depends of libespeak1
      Installing libjack-jackd2-0 as Depends of libportaudio2
    Installing espeak-data as Depends of libespeak1
  Installing language-pack-gnome-en as Depends of language-pack-gnome-en-base
    Installing language-pack-en-base as Depends of language-pack-gnome-en
      Installing language-pack-en as Depends of language-pack-en-base
  Installing erlang-base as Depends of erlang-crypto
    previously satisfied important dependency on erlang-syntax-tools
    Installing erlang-syntax-tools as Recommends of erlang-base
  Installing xserver-xorg-core as Depends of xserver-xorg-video-apm
    Installing xserver-common as Depends of xserver-xorg-core
    Installing libxfont1 as Depends of xserver-xorg-core
      Installing libdrm-intel1 as Depends of xserver-xorg-video-intel
      Installing libdrm-nouveau1 as Depends of xserver-xorg-video-nouveau
  Installing gnome-games-common as Depends of gnome-mahjongg
  Installing libnice0 as Depends of telepathy-gabble
    Installing libgssdp-1.0-2 as Depends of libnice0
    Installing libgupnp-1.0-3 as Depends of libnice0
    Installing libgupnp-igd-1.0-3 as Depends of libnice0
  Installing libtelepathy-glib0 as Depends of telepathy-gabble
    Installing libmission-control-plugins0 as Depends of telepathy-mission-control-5
  Installing nautilus-data as Depends of nautilus
  Installing libgnome2-common as Depends of libgnome2-0
  Installing libprotobuf6 as Depends of libcompizconfig0
  Installing compiz-core as Depends of libcompizconfig0
    previously satisfied important dependency on compiz-plugins
    Installing compiz-plugins as Recommends of compiz-core
  Installing checkbox as Depends of checkbox-gtk
  Installing libbind9-60 as Depends of bind9-host
    Installing libdns66 as Depends of libbind9-60
      Installing libgeoip1 as Depends of libdns66
  Installing libisc60 as Depends of bind9-host
  Installing libisccfg60 as Depends of bind9-host
  Installing liblwres60 as Depends of bind9-host
  Installing libcamel1.2-14 as Depends of evolution-indicator
    Installing libedataserver1.2-13 as Depends of libcamel1.2-14
  Installing libevolution as Depends of evolution-indicator
    Installing libebackend1.2-0 as Depends of libevolution
    Installing libebook1.2-9 as Depends of libevolution
    Installing libecal1.2-7 as Depends of libevolution
    Installing libedataserverui1.2-8 as Depends of libevolution
    Installing libgdata-google1.2-1 as Depends of libevolution
      Installing libgdata1.2-1 as Depends of libgdata-google1.2-1
    Installing libgtkhtml-editor0 as Depends of libevolution
      Installing libgtkhtml3.14-19 as Depends of libgtkhtml-editor0
      Installing libgtkhtml-editor-common as Depends of libgtkhtml-editor0
  Installing libncursesw5 as Depends of procps
  Installing gvfs as Depends of gvfs-fuse
  Installing python-markupsafe as Depends of python-mako
    Installing python as Depends of python-markupsafe
      Installing python2.6 as Depends of python
        Installing python2.6-minimal as Depends of python2.6
      Installing python-minimal as Depends of python
  Installing libaspell15 as Depends of aspell
  Installing libusb-1.0-0 as Depends of usbmuxd
  Installing libdirectfb-1.2-9 as Depends of gstreamer0.10-plugins-bad
  Installing libgstreamer-plugins-base0.10-0 as Depends of gstreamer0.10-plugins-bad
    Installing libgstreamer0.10-0 as Depends of libgstreamer-plugins-base0.10-0
  Installing libmodplug1 as Depends of gstreamer0.10-plugins-bad
  Installing libmpcdec6 as Depends of gstreamer0.10-plugins-bad
  Installing liborc-0.4-0 as Depends of gstreamer0.10-plugins-bad
  Installing librtmp0 as Depends of gstreamer0.10-plugins-bad
  Installing libvpx0 as Depends of gstreamer0.10-plugins-bad
  Installing libzbar0 as Depends of gstreamer0.10-plugins-bad
  Installing python-ubuntuone-storageprotocol as Depends of python-ubuntuone-client
  Installing python-libproxy as Depends of python-ubuntuone-client
  Installing libpoppler7 as Depends of poppler-utils
  Installing ubuntu-sso-client as Depends of ubuntuone-client
    Installing dpkg as PreDepends of ubuntu-sso-client
  Installing libsnmp-base as Depends of libsnmp15
  Installing libgnome-bluetooth8 as Depends of network-manager-gnome
  Installing libnm-glib2 as Depends of network-manager-gnome
  Installing libnm-util1 as Depends of network-manager-gnome
  Installing librasqal2 as Depends of librdf0
  Installing esound-common as Depends of esound-clients
  Installing samba-common as Depends of smbclient
  Installing libnewt0.52 as Depends of whiptail
  Installing libcanberra0 as Depends of libcanberra-pulse
  Installing libatspi1.0-0 as Depends of brltty-x11
  Installing brltty as Depends of brltty-x11
  Installing totem as Depends of totem-plugins
    Installing libtotem-plparser17 as Depends of totem
    Installing gstreamer0.10-plugins-base as Depends of totem
    Installing totem-common as Depends of totem
    previously satisfied important dependency on totem-mozilla
    Installing totem-mozilla as Recommends of totem
  Installing libgdata7 as Depends of totem-plugins
  Installing gdebi-core as Depends of gdebi
    Installing python-apt as Depends of gdebi-core
      Installing apt-utils as Depends of python-apt
  Installing libimobiledevice1 as Depends of upower
  Installing libupower-glib1 as Depends of upower
  Installing libpulse0 as Depends of pulseaudio-module-bluetooth
  Installing xul-ext-ubufox as Depends of ubufox
  Installing libegroupwise1.2-13 as Depends of evolution
  Installing evolution-common as Depends of evolution
  Installing evolution-data-server as Depends of evolution
    Installing libedata-book1.2-2 as Depends of evolution-data-server
    Installing libedata-cal1.2-7 as Depends of evolution-data-server
    Installing evolution-data-server-common as Depends of evolution-data-server
  Installing libmagickcore3 as Depends of obex-data-server
    Installing liblqr-1-0 as Depends of libmagickcore3
  Installing libmagickwand3 as Depends of obex-data-server
  Installing libglib-perl as Depends of libgtk2-perl
  Installing libgwibber0 as Depends of indicator-me
    Installing gwibber-service as Depends of libgwibber0
  Installing gcc-4.4-base as Depends of g++-4.4
  Installing gcc-4.4 as Depends of g++-4.4
    Installing cpp-4.4 as Depends of gcc-4.4
      Installing libmpfr4 as Depends of cpp-4.4
    Installing binutils as Depends of gcc-4.4
    Installing libgcc1 as Depends of gcc-4.4
    Installing libgomp1 as Depends of gcc-4.4
  Installing libstdc++6-4.4-dev as Depends of g++-4.4
  Installing libgnomekbd4 as Depends of gnome-settings-daemon
    Installing libgnomekbd-common as Depends of libgnomekbd4
  Installing at-spi as Depends of python-pyatspi
  Installing liblouis2 as Depends of python-louis
  Installing libutempter0 as Depends of xterm
  Installing python-gmenu as Depends of gnome-menus
  Installing speech-dispatcher as Depends of python-speechd
  Installing libvte9 as Depends of gnome-terminal
  Installing gnome-terminal-data as Depends of gnome-terminal
  Installing gnome-session-common as Depends of gnome-session
  Installing libhpmud0 as Depends of hpijs
  Installing linux-image-generic as Depends of linux-generic
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing linux-image-2.6.35-24-generic as Depends of linux-image-generic
    Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing cups-common as Depends of cups-client
  Installing python-lazr.restfulclient as Depends of python-launchpadlib
  Installing libgoocanvas-common as Depends of libgoocanvas3
  Installing libindicate4 as Depends of python-indicate
  Installing transmission-common as Depends of transmission-gtk
  Installing libsane-hpaio as Depends of hplip
  Installing hplip-data as Depends of hplip
  Installing mono-csharp-shell as Depends of gbrainy
    Installing libmono-management2.0-cil as Depends of mono-csharp-shell
    Installing mono-gmcs as Depends of mono-csharp-shell
  Installing libboost-iostreams1.42.0 as Depends of aptitude
  Installing libept1 as Depends of aptitude
  Installing libfolks-telepathy0 as Depends of empathy
    Installing libfolks0 as Depends of libfolks-telepathy0
  Installing libtelepathy-logger1 as Depends of empathy
  Installing gnome-icon-theme as Depends of empathy
  Installing telepathy-logger as Depends of empathy
  Installing gnome-utils-common as Depends of libgdict-1.0-6
  Installing usb-creator-common as Depends of usb-creator-gtk
  Installing python-aptdaemon as Depends of software-center
  Installing aptdaemon as Depends of software-center
  previously satisfied important dependency on apt-xapian-index
  Installing apt-xapian-index as Recommends of software-center
  new important dependency: sessioninstaller
  Installing sessioninstaller as Recommends of software-center
    Installing python-aptdaemon-gtk as Depends of sessioninstaller
  Installing cpp as Depends of g++
  Installing gcc as Depends of g++
  Installing libplymouth2 as Depends of plymouth-label
  Installing plymouth as Depends of plymouth-label
  Installing libbluetooth3 as Depends of bluez
  Installing firefox as Depends of firefox-branding
  Installing e2fslibs as PreDepends of e2fsprogs
  Installing grub-common as Depends of grub-pc
  Installing mysql-common as Depends of libmysqlclient16
  Installing libva1 as Depends of libavcodec52
  Installing update-manager-core as Depends of update-manager
  Installing baobab as Depends of gnome-utils
  Installing gnome-dictionary as Depends of gnome-utils
  Installing gnome-screenshot as Depends of gnome-utils
  Installing gnome-search-tool as Depends of gnome-utils
  Installing gnome-system-log as Depends of gnome-utils
  Installing libasound2 as Depends of lib32asound2
  new important dependency: gpg
  Installing libclutter-1.0-0 as Depends of libclutter-gtk-0.10-0
  Installing python-gtk2 as Depends of python-glade2
  Installing libavformat52 as Depends of gstreamer0.10-ffmpeg
  Installing libpostproc51 as Depends of gstreamer0.10-ffmpeg
  Installing python-papyon as Depends of telepathy-butterfly
  Installing gnome-desktop-data as Depends of gnome-about
  new important dependency: hwdata
  Installing hwdata as Recommends of libgnome-desktop-2-17
  Installing libsdl1.2debian-alsa as Depends of libsdl1.2debian
  Installing liboobs-1-5 as Depends of gnome-system-tools
    Installing cups-ppdc as Depends of cups
  Installing libxapian15 as Depends of python-xapian
  Installing libutouch-grail1 as Depends of xserver-xorg-input-evdev
    Installing libmtdev1 as Depends of libutouch-grail1
  new important dependency: usb-modeswitch
  Installing usb-modeswitch as Recommends of modemmanager
    Installing usb-modeswitch-data as Depends of usb-modeswitch
  Installing libsyncdaemon-1.0-1 as Depends of libubuntuone-1.0-1
  Installing linux-headers-2.6.35-24-generic as Depends of linux-headers-generic
    Installing linux-headers-2.6.35-24 as Depends of linux-headers-2.6.35-24-generic
  Installing libdjvulibre-text as Depends of libdjvulibre21
  Installing libevdocument3 as Depends of evince
    Installing libpoppler-glib5 as Depends of libevdocument3
    Installing libt1-5 as Depends of libevdocument3
  Installing libevview3 as Depends of evince
  Installing evince-common as Depends of evince
  Installing libvorbis0a as Depends of libvorbisfile3
  Installing libnih1 as Depends of libnih-dbus1
  Installing initramfs-tools-bin as Depends of initramfs-tools
  Installing libgladeui-1-9 as Depends of libgnome-media0
  Installing libgimp2.0 as Depends of gimp
    previously satisfied important dependency on gimp-data
    Installing gimp-data as Recommends of libgimp2.0
  Installing libmng1 as Depends of gimp
  Installing libgirepository1.0-1 as Depends of python-gobject
  Installing gir1.0-glib-2.0 as Depends of python-gobject
  new important dependency: python-gobject-cairo
  Installing python-gobject-cairo as Recommends of python-gobject
  Installing erlang-ssl as Depends of erlang-inets
  Installing dhcp3-common as Depends of dhcp3-client
  previously satisfied important dependency on indicator-application
  Installing libc-dev-bin as Depends of libc6-dev
  Installing libavahi-core7 as Depends of avahi-daemon
  Installing gsfonts as Depends of ghostscript
  Installing libtag1-vanilla as Depends of libtag1c2a
  Installing computer-janitor as Depends of computer-janitor-gtk
    Installing python-argparse as Depends of computer-janitor
  previously satisfied important dependency on libsasl2-modules
  Installing libsasl2-modules as Recommends of libsasl2-2
  Installing libprotoc6 as Depends of protobuf-compiler
  Installing capplets-data as Depends of gnome-control-center
  new important dependency: libmagickcore3-extra
  Installing libmagickcore3-extra as Recommends of imagemagick
    Installing libcdt4 as Depends of libmagickcore3-extra
    Installing libgraph4 as Depends of libmagickcore3-extra
    Installing libgvc5 as Depends of libmagickcore3-extra
      Installing libpathplan4 as Depends of libgvc5
      Installing libxdot4 as Depends of libgvc5
  new important dependency: netpbm
  Installing netpbm as Recommends of imagemagick
    Installing libnetpbm10 as Depends of netpbm
  Installing libbrasero-media1 as Depends of brasero
    Installing libburn4 as Depends of libbrasero-media1
    Installing libisofs6 as Depends of libbrasero-media1
  new important dependency: brasero-cdrkit
  Installing brasero-cdrkit as Recommends of brasero
  Installing libdmapsharing2 as Depends of rhythmbox-plugins
  Installing libvala-0.10-0 as Depends of rhythmbox-plugins
  Installing mysql-client-5.1 as Depends of mysql-server-5.1
  Installing libntfs-3g79 as Depends of ntfs-3g
Starting
Starting 2
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 75
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating pm-utils
Package pm-utils has broken Conflicts on pm-utils-powersave-policy
  Considering pm-utils-powersave-policy -1 as a solution to pm-utils 9
  Added pm-utils-powersave-policy to the remove list
  Fixing pm-utils via remove of pm-utils-powersave-policy
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-video-all 5
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-video-all via keep of xserver-xorg-video-tseng
Investigating foomatic-db-compressed-ppds
Package foomatic-db-compressed-ppds has broken Conflicts on foomatic-db
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Added foomatic-db to the remove list
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
Package foomatic-db-compressed-ppds has broken Conflicts on foomatic-db-hpijs
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Added foomatic-db to the remove list
  Fixing foomatic-db-compressed-ppds via remove of foomatic-db
  Fixing foomatic-db-compressed-ppds via remove of foomatic-db
Investigating libcdt4
Package libcdt4 has broken Conflicts on libgraphviz4
  Considering libgraphviz4 1 as a solution to libcdt4 3
  Added libgraphviz4 to the remove list
  Fixing libcdt4 via remove of libgraphviz4
Investigating libept0
Package libept0 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 31 as a solution to libept0 3
  Removing libept0 rather than change libapt-pkg-libc6.10-6-4.8
 Try to Re-Instate xserver-xorg-video-tseng
Re-Instated xserver-xorg-video-tseng (3 vs 3)
Investigating libbrasero-media0
Package libbrasero-media0 has broken Depends on brasero-common
  Considering brasero-common 14 as a solution to libbrasero-media0 -1
  Removing libbrasero-media0 rather than change brasero-common
Investigating libmagickcore2-extra
Package libmagickcore2-extra has broken Depends on libgraphviz4
  Considering libgraphviz4 1 as a solution to libmagickcore2-extra -1
  Removing libmagickcore2-extra rather than change libgraphviz4
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 75
  Added xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-video-all 5
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-video-all via keep of xserver-xorg-video-tseng
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 75
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 75 as a solution to xserver-xorg-video-all 5
  Removing xserver-xorg-video-all rather than change xserver-xorg-video-tseng
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 75 as a solution to xserver-xorg-core 75
  Holding Back xserver-xorg-core rather than change xserver-xorg-video-6
Investigating xserver-xorg
Package xserver-xorg has broken Depends on xserver-xorg-core
  Considering xserver-xorg-core 75 as a solution to xserver-xorg 44
  Holding Back xserver-xorg rather than change xserver-xorg-core
Investigating xserver-xorg-input-evdev
Package xserver-xorg-input-evdev has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-input-evdev 7
  Holding Back xserver-xorg-input-evdev rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-apm
Package xserver-xorg-video-apm has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-apm 2
  Holding Back xserver-xorg-video-apm rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ark
Package xserver-xorg-video-ark has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-ark 2
  Holding Back xserver-xorg-video-ark rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ati
Package xserver-xorg-video-ati has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-ati 2
  Holding Back xserver-xorg-video-ati rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-openchrome 2
  Holding Back xserver-xorg-video-openchrome rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3virge
Package xserver-xorg-video-s3virge has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-s3virge 2
  Holding Back xserver-xorg-video-s3virge rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-mga
Package xserver-xorg-video-mga has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-mga 2
  Holding Back xserver-xorg-video-mga rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-chips
Package xserver-xorg-video-chips has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-chips 2
  Holding Back xserver-xorg-video-chips rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-mach64
Package xserver-xorg-video-mach64 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-mach64 2
  Holding Back xserver-xorg-video-mach64 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-trident
Package xserver-xorg-video-trident has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-trident 2
  Holding Back xserver-xorg-video-trident rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-sis
Package xserver-xorg-video-sis has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-sis 2
  Holding Back xserver-xorg-video-sis rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-siliconmotion
Package xserver-xorg-video-siliconmotion has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-siliconmotion 2
  Holding Back xserver-xorg-video-siliconmotion rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-vmmouse
Package xserver-xorg-input-vmmouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-input-vmmouse 2
  Holding Back xserver-xorg-input-vmmouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-savage
Package xserver-xorg-video-savage has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-savage 2
  Holding Back xserver-xorg-video-savage rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-tdfx
Package xserver-xorg-video-tdfx has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-tdfx 2
  Holding Back xserver-xorg-video-tdfx rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-intel
Package xserver-xorg-video-intel has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-intel 2
  Holding Back xserver-xorg-video-intel rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vmware
Package xserver-xorg-video-vmware has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-vmware 2
  Holding Back xserver-xorg-video-vmware rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-r128
Package xserver-xorg-video-r128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-r128 2
  Holding Back xserver-xorg-video-r128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vesa
Package xserver-xorg-video-vesa has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-vesa 2
  Holding Back xserver-xorg-video-vesa rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3
Package xserver-xorg-video-s3 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-s3 2
  Holding Back xserver-xorg-video-s3 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-nv
Package xserver-xorg-video-nv has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nv 2
  Holding Back xserver-xorg-video-nv rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-voodoo
Package xserver-xorg-video-voodoo has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-voodoo 2
  Holding Back xserver-xorg-video-voodoo rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-fbdev
Package xserver-xorg-video-fbdev has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-fbdev 2
  Holding Back xserver-xorg-video-fbdev rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-wacom
Package xserver-xorg-input-wacom has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-input-wacom 2
  Holding Back xserver-xorg-input-wacom rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-neomagic
Package xserver-xorg-video-neomagic has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-neomagic 2
  Holding Back xserver-xorg-video-neomagic rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-mouse
Package xserver-xorg-input-mouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-input-mouse 2
  Holding Back xserver-xorg-input-mouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-sisusb
Package xserver-xorg-video-sisusb has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-sisusb 2
  Holding Back xserver-xorg-video-sisusb rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-radeon
Package xserver-xorg-video-radeon has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-radeon 2
  Holding Back xserver-xorg-video-radeon rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-cirrus
Package xserver-xorg-video-cirrus has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-cirrus 2
  Holding Back xserver-xorg-video-cirrus rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-synaptics
Package xserver-xorg-input-synaptics has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-input-synaptics 2
  Holding Back xserver-xorg-input-synaptics rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-rendition
Package xserver-xorg-video-rendition has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-rendition 2
  Holding Back xserver-xorg-video-rendition rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-i128
Package xserver-xorg-video-i128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-i128 2
  Holding Back xserver-xorg-video-i128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-v4l
Package xserver-xorg-video-v4l has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-v4l 0
  Holding Back xserver-xorg-video-v4l rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-core
 Try to Re-Instate xserver-xorg
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
 Try to Re-Instate xserver-xorg-input-evdev
 Try to Re-Instate xserver-xorg-video-apm
 Try to Re-Instate xserver-xorg-video-ark
 Try to Re-Instate xserver-xorg-video-ati
 Try to Re-Instate xserver-xorg-video-openchrome
 Try to Re-Instate xserver-xorg-video-s3virge
 Try to Re-Instate xserver-xorg-video-mga
 Try to Re-Instate xserver-xorg-video-chips
 Try to Re-Instate xserver-xorg-video-mach64
 Try to Re-Instate xserver-xorg-video-trident
 Try to Re-Instate xserver-xorg-video-sis
 Try to Re-Instate xserver-xorg-video-siliconmotion
 Try to Re-Instate xserver-xorg-input-vmmouse
 Try to Re-Instate xserver-xorg-video-savage
 Try to Re-Instate xserver-xorg-video-tdfx
 Try to Re-Instate xserver-xorg-video-intel
 Try to Re-Instate xserver-xorg-video-vmware
 Try to Re-Instate xserver-xorg-video-r128
 Try to Re-Instate xserver-xorg-video-vesa
 Try to Re-Instate xserver-xorg-video-s3
 Try to Re-Instate xserver-xorg-video-nv
 Try to Re-Instate xserver-xorg-video-voodoo
 Try to Re-Instate xserver-xorg-video-fbdev
 Try to Re-Instate xserver-xorg-input-wacom
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-video-neomagic
 Try to Re-Instate xserver-xorg-input-mouse
 Try to Re-Instate xserver-xorg-video-sisusb
 Try to Re-Instate xserver-xorg-video-radeon
 Try to Re-Instate xserver-xorg-video-cirrus
 Try to Re-Instate xserver-xorg-input-synaptics
 Try to Re-Instate xserver-xorg-video-rendition
 Try to Re-Instate xserver-xorg-video-i128
 Try to Re-Instate xserver-xorg-video-v4l
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Done
Log time: 2011-01-18 18:34:27.037149rver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-video-all 5
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-video-all via keep of xserver-xorg-video-tseng
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 75
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 75 as a solution to xserver-xorg-video-all 5
  Removing xserver-xorg-video-all rather than change xserver-xorg-video-tseng
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 75 as a solution to xserver-xorg-core 75
  Holding Back xserver-xorg-core rather than change xserver-xorg-video-6
Investigating xserver-xorg
Package xserver-xorg has broken Depends on xserver-xorg-core
  Considering xserver-xorg-core 75 as a solution to xserver-xorg 44
  Holding Back xserver-xorg rather than change xserver-xorg-core
Investigating xserver-xorg-input-evdev
Package xserver-xorg-input-evdev has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-input-evdev 7
  Holding Back xserver-xorg-input-evdev rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-apm
Package xserver-xorg-video-apm has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-apm 2
  Holding Back xserver-xorg-video-apm rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ark
Package xserver-xorg-video-ark has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-ark 2
  Holding Back xserver-xorg-video-ark rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ati
Package xserver-xorg-video-ati has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-ati 2
  Holding Back xserver-xorg-video-ati rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-openchrome 2
  Holding Back xserver-xorg-video-openchrome rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3virge
Package xserver-xorg-video-s3virge has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-s3virge 2
  Holding Back xserver-xorg-video-s3virge rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-mga
Package xserver-xorg-video-mga has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-mga 2
  Holding Back xserver-xorg-video-mga rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-chips
Package xserver-xorg-video-chips has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-chips 2
  Holding Back xserver-xorg-video-chips rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-mach64
Package xserver-xorg-video-mach64 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-mach64 2
  Holding Back xserver-xorg-video-mach64 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-trident
Package xserver-xorg-video-trident has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-trident 2
  Holding Back xserver-xorg-video-trident rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-sis
Package xserver-xorg-video-sis has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-sis 2
  Holding Back xserver-xorg-video-sis rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-siliconmotion
Package xserver-xorg-video-siliconmotion has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-siliconmotion 2
  Holding Back xserver-xorg-video-siliconmotion rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-vmmouse
Package xserver-xorg-input-vmmouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-input-vmmouse 2
  Holding Back xserver-xorg-input-vmmouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-savage
Package xserver-xorg-video-savage has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-savage 2
  Holding Back xserver-xorg-video-savage rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-tdfx
Package xserver-xorg-video-tdfx has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-tdfx 2
  Holding Back xserver-xorg-video-tdfx rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-intel
Package xserver-xorg-video-intel has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-intel 2
  Holding Back xserver-xorg-video-intel rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vmware
Package xserver-xorg-video-vmware has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-vmware 2
  Holding Back xserver-xorg-video-vmware rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-r128
Package xserver-xorg-video-r128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-r128 2
  Holding Back xserver-xorg-video-r128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vesa
Package xserver-xorg-video-vesa has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-vesa 2
  Holding Back xserver-xorg-video-vesa rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3
Package xserver-xorg-video-s3 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-s3 2
  Holding Back xserver-xorg-video-s3 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-nv
Package xserver-xorg-video-nv has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nv 2
  Holding Back xserver-xorg-video-nv rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-voodoo
Package xserver-xorg-video-voodoo has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-voodoo 2
  Holding Back xserver-xorg-video-voodoo rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-fbdev
Package xserver-xorg-video-fbdev has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-fbdev 2
  Holding Back xserver-xorg-video-fbdev rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-wacom
Package xserver-xorg-input-wacom has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-input-wacom 2
  Holding Back xserver-xorg-input-wacom rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-neomagic
Package xserver-xorg-video-neomagic has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-neomagic 2
  Holding Back xserver-xorg-video-neomagic rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-mouse
Package xserver-xorg-input-mouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-input-mouse 2
  Holding Back xserver-xorg-input-mouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-sisusb
Package xserver-xorg-video-sisusb has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-sisusb 2
  Holding Back xserver-xorg-video-sisusb rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-radeon
Package xserver-xorg-video-radeon has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-radeon 2
  Holding Back xserver-xorg-video-radeon rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-cirrus
Package xserver-xorg-video-cirrus has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-cirrus 2
  Holding Back xserver-xorg-video-cirrus rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-synaptics
Package xserver-xorg-input-synaptics has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-input-synaptics 2
  Holding Back xserver-xorg-input-synaptics rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-rendition
Package xserver-xorg-video-rendition has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-rendition 2
  Holding Back xserver-xorg-video-rendition rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-i128
Package xserver-xorg-video-i128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-i128 2
  Holding Back xserver-xorg-video-i128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-v4l
Package xserver-xorg-video-v4l has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-v4l 0
  Holding Back xserver-xorg-video-v4l rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-core
 Try to Re-Instate xserver-xorg
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
 Try to Re-Instate xserver-xorg-input-evdev
 Try to Re-Instate xserver-xorg-video-apm
 Try to Re-Instate xserver-xorg-video-ark
 Try to Re-Instate xserver-xorg-video-ati
 Try to Re-Instate xserver-xorg-video-openchrome
 Try to Re-Instate xserver-xorg-video-s3virge
 Try to Re-Instate xserver-xorg-video-mga
 Try to Re-Instate xserver-xorg-video-chips
 Try to Re-Instate xserver-xorg-video-mach64
 Try to Re-Instate xserver-xorg-video-trident
 Try to Re-Instate xserver-xorg-video-sis
 Try to Re-Instate xserver-xorg-video-siliconmotion
 Try to Re-Instate xserver-xorg-input-vmmouse
 Try to Re-Instate xserver-xorg-video-savage
 Try to Re-Instate xserver-xorg-video-tdfx
 Try to Re-Instate xserver-xorg-video-intel
 Try to Re-Instate xserver-xorg-video-vmware
 Try to Re-Instate xserver-xorg-video-r128
 Try to Re-Instate xserver-xorg-video-vesa
 Try to Re-Instate xserver-xorg-video-s3
 Try to Re-Instate xserver-xorg-video-nv
 Try to Re-Instate xserver-xorg-video-voodoo
 Try to Re-Instate xserver-xorg-video-fbdev
 Try to Re-Instate xserver-xorg-input-wacom
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-video-neomagic
 Try to Re-Instate xserver-xorg-input-mouse
 Try to Re-Instate xserver-xorg-video-sisusb
 Try to Re-Instate xserver-xorg-video-radeon
 Try to Re-Instate xserver-xorg-video-cirrus
 Try to Re-Instate xserver-xorg-input-synaptics
 Try to Re-Instate xserver-xorg-video-rendition
 Try to Re-Instate xserver-xorg-video-i128
 Try to Re-Instate xserver-xorg-video-v4l
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 75 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Done
Log time: 2011-01-18 18:34:27.037149

```

Any help figuring out what might be holding me up would be greatly appreciated.

Thank you.

---

### Post by Cheesehead on 2011-01-19
From your apt.log, your system seems to be choking on:
libdrm-nouveau1
xserver-xorg-video-nouveau

Normally, I would purge the old/ppa/funky-broken packages, upgrade cleanly, then re-install the packages after the upgrade.
But in this case, we're messing with your video. My solution breaks your video during the upgrade...and that may be outside your comfort zone.

---

