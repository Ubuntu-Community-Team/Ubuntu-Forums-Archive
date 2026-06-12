---
title: "attempting upgrade from 10.04 to 10.10"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by moth17 on 2011-02-23
Getting error:

> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.


Not sure how to go about "please report this bug against the 'update-manager' package"

Looking at the logs in "/var/log/dist-upgrade/" yields:

apt.log:
```
Log time: 2011-02-23 11:56:55.494868
Log time: 2011-02-23 11:57:00.715832
Log time: 2011-02-23 11:57:14.699269
  Installing xserver-xorg-core as Depends of xserver-xorg
    Installing xserver-common as Depends of xserver-xorg-core
    Installing libxfont1 as Depends of xserver-xorg-core
      Installing libdrm-intel1 as Depends of xserver-xorg-video-intel
      Installing libxcb-dri2-0 as Depends of xserver-xorg-video-intel
      Installing libdrm-nouveau1 as Depends of xserver-xorg-video-nouveau
  Installing gconf2 as Depends of ubuntuone-client
    Installing libgconf2-4 as Depends of gconf2
      Installing libglib2.0-0 as Depends of libgconf2-4
        new important dependency: libdconf0
        Installing libdconf0 as Recommends of libglib2.0-0
      Installing gconf2-common as Depends of libgconf2-4
  Installing python-ubuntuone-client as Depends of ubuntuone-client
    Installing python-ubuntuone-storageprotocol as Depends of python-ubuntuone-client
    Installing python-libproxy as Depends of python-ubuntuone-client
  Installing ubuntu-sso-client as Depends of ubuntuone-client
    Installing dpkg as PreDepends of ubuntu-sso-client
      Installing xz-utils as PreDepends of dpkg
        Installing liblzma2 as Depends of xz-utils
  Installing libsgutils2-2 as Depends of sg3-utils
  Installing libappindicator1 as Depends of policykit-1-gnome
    Installing libdbus-glib-1-2 as Depends of libappindicator1
    Installing libdbusmenu-glib1 as Depends of libappindicator1
    Installing libdbusmenu-gtk1 as Depends of libappindicator1
      Installing libgdk-pixbuf2.0-0 as Depends of libdbusmenu-gtk1
    Installing libindicator1 as Depends of libappindicator1
    Installing indicator-application as Recommends of libappindicator1
  Installing libc6 as Depends of mono-2.0-gac
    Installing libc-bin as Depends of libc6
  Installing libmono-corlib2.0-cil as Depends of mono-2.0-gac
    Installing mono-runtime as Depends of libmono-corlib2.0-cil
      Installing mono-gac as Depends of mono-runtime
  Installing libmono-security2.0-cil as Depends of mono-2.0-gac
    Installing libmono-system2.0-cil as Depends of libmono-security2.0-cil
  Installing libcairo2 as Depends of f-spot
    Installing libpixman-1-0 as Depends of libcairo2
  Installing libgtk2.0-0 as Depends of f-spot
  Installing libglib2.0-cil as Depends of f-spot
  Installing libgtk2.0-cil as Depends of f-spot
  Installing libmono-simd2.0-cil as Depends of f-spot
  Installing libmono-system-data2.0-cil as Depends of f-spot
    Installing libmono-data-tds2.0-cil as Depends of libmono-system-data2.0-cil
    Installing libmono-wcf3.0-cil as Depends of libmono-system-data2.0-cil
      Installing libmono-system-messaging2.0-cil as Depends of libmono-wcf3.0-cil
        Installing libmono-messaging2.0-cil as Depends of libmono-system-messaging2.0-cil
  Installing libsqlite3-0 as Depends of f-spot
  Installing libgstreamer0.10-0 as Depends of gstreamer0.10-alsa
  Installing libgstreamer-plugins-base0.10-0 as Depends of gstreamer0.10-alsa
  Installing libsdl1.2debian-alsa as Depends of libsdl1.2debian
  Installing libakonadi-kcal4 as Depends of plasma-dataengines-workspace
    Installing libkcal4 as Depends of libakonadi-kcal4
      Installing libkabc4 as Depends of libkcal4
        Installing libkdecore5 as Depends of libkabc4
          Installing libqt4-dbus as Depends of libkdecore5
            Installing libqt4-xml as Depends of libqt4-dbus
              Installing libqtcore4 as Depends of libqt4-xml
          Installing libqt4-network as Depends of libkdecore5
        Installing libkdeui5 as Depends of libkabc4
          Installing libdbusmenu-qt2 as Depends of libkdeui5
            Installing libqtgui4 as Depends of libdbusmenu-qt2
              Installing libmng1 as Depends of libqtgui4
          Installing libqt4-svg as Depends of libkdeui5
          Installing kdelibs5-data as Recommends of libkdeui5
        Installing libkio5 as Depends of libkabc4
          Installing libnepomuk4 as Depends of libkio5
            Installing libsoprano4 as Depends of libnepomuk4
              Installing soprano-daemon as Depends of libsoprano4
          Installing libsolid4 as Depends of libkio5
          Installing kdelibs5-plugins as Recommends of libkio5
            Installing libkatepartinterfaces4 as Depends of kdelibs5-plugins
              Installing libkparts4 as Depends of libkatepartinterfaces4
              Installing libktexteditor4 as Depends of libkatepartinterfaces4
              Installing libkutils4 as Depends of libkatepartinterfaces4
              Installing libqt4-script as Depends of libkatepartinterfaces4
            Installing libkfile4 as Depends of kdelibs5-plugins
            Installing libkhtml5 as Depends of kdelibs5-plugins
              Installing libkjsapi4 as Depends of libkhtml5
              Installing libphonon4 as Depends of libkhtml5
            Installing libkjsembed4 as Depends of kdelibs5-plugins
            Installing libkntlm4 as Depends of kdelibs5-plugins
            Installing libkrosscore4 as Depends of kdelibs5-plugins
            Installing libkrossui4 as Depends of kdelibs5-plugins
            Installing kdoctools as Depends of kdelibs5-plugins
              Installing docbook-xsl as Depends of kdoctools
                Installing docbook-xsl-doc-html as Recommends of docbook-xsl
            Installing kdelibs-bin as Depends of kdelibs5-plugins
        Installing libkldap4 as Depends of libkabc4
        Installing libkresources4 as Depends of libkabc4
      Installing libkpimutils4 as Depends of libkcal4
        Installing libkmime4 as Depends of libkpimutils4
  Installing libakonadi-kde4 as Depends of plasma-dataengines-workspace
    Installing libakonadiprivate1 as Depends of libakonadi-kde4
      Installing libboost-program-options1.42.0 as Depends of libakonadiprivate1
      Installing libqt4-sql as Depends of libakonadiprivate1
  Installing libakonadi-kmime4 as Depends of plasma-dataengines-workspace
  Installing libgps19 as Depends of plasma-dataengines-workspace
  Installing libkholidays4 as Depends of plasma-dataengines-workspace
  Installing libksgrd4 as Depends of plasma-dataengines-workspace
  Installing libmicroblog4 as Depends of plasma-dataengines-workspace
  Installing libplasma-geolocation-interface4 as Depends of plasma-dataengines-workspace
  Installing libplasma3 as Depends of plasma-dataengines-workspace
    Installing libkdewebkit5 as Depends of libplasma3
      Installing libqtwebkit4 as Depends of libkdewebkit5
    Installing libkdnssd4 as Depends of libplasma3
    Installing libknewstuff3-4 as Depends of libplasma3
      Installing libattica0 as Depends of libknewstuff3-4
    Installing libqt4-opengl as Depends of libplasma3
    Installing libthreadweaver4 as Depends of libplasma3
  Installing libsolidcontrol4a as Depends of plasma-dataengines-workspace
    Installing libsolidcontrolifaces4 as Depends of libsolidcontrol4a
  Installing libsyndication4 as Depends of plasma-dataengines-workspace
  Installing libtaskmanager4a as Depends of plasma-dataengines-workspace
    Installing libkephal4 as Depends of libtaskmanager4a
  Installing libweather-ion4a as Depends of plasma-dataengines-workspace
  previously satisfied important dependency on ksysguardd
  Installing ksysguardd as Recommends of plasma-dataengines-workspace
  Installing libkrb5support0 as Depends of libkrb5-3
  Installing libgnomekbd-common as Depends of libgnomekbd4
  Installing perl as Depends of libpurple0
    Installing perl-base as Depends of perl
    Installing perl-modules as Depends of perl
  Installing python as Depends of python-twisted-names
    Installing python2.6 as Depends of python
      Installing python2.6-minimal as Depends of python2.6
        Installing libssl0.9.8 as Depends of python2.6-minimal
      Installing libncursesw5 as Depends of python2.6
    Installing python-minimal as Depends of python
  Installing python-twisted-core as Depends of python-twisted-names
    Installing python-twisted-bin as Depends of python-twisted-core
  Installing syslinux-common as Depends of syslinux
    Installing libcrypt-passwdmd5-perl as Recommends of syslinux-common
    Installing libdigest-sha1-perl as Recommends of syslinux-common
  Installing libavutil50 as Depends of libswscale0
  Installing gcc-4.5-base as Depends of libstdc++6
  Installing libmono-system1.0-cil as Depends of libmono-posix1.0-cil
  Installing libqapt1 as Depends of kubuntu-debug-installer
    Installing apt as Depends of libqapt1
      new important dependency: gpg
  Installing qapt-batch as Depends of kubuntu-debug-installer
    Installing libqapt-runtime as Depends of qapt-batch
  Installing libappindicator0.1-cil as Depends of tomboy
  Installing libbz2-1.0 as Depends of bzip2
  Installing libedataserver1.2-13 as Depends of evolution-webcal
  Installing libebook1.2-9 as Depends of ekiga
    Installing libcamel1.2-14 as Depends of libebook1.2-9
  Installing libnotify1 as Depends of ekiga
  Installing libopal3.6.8 as Depends of ekiga
    Installing libpt2.6.7 as Depends of libopal3.6.8
    Installing libsrtp0 as Depends of libopal3.6.8
  Installing libespeak1 as Depends of espeak
    Installing libportaudio2 as Depends of libespeak1
      Installing libjack-jackd2-0 as Depends of libportaudio2
    Installing espeak-data as Depends of libespeak1
  Installing libnih1 as Depends of libnih-dbus1
  Installing computer-janitor as Depends of computer-janitor-gtk
    Installing python-argparse as Depends of computer-janitor
  Installing openoffice.org-core as Depends of openoffice.org-gnome
    Installing openoffice.org-common as Depends of openoffice.org-core
    Installing libhunspell-1.2-0 as Depends of openoffice.org-core
    Installing libneon27-gnutls as Depends of openoffice.org-core
    Installing ure as Depends of openoffice.org-core
      Installing uno-libs3 as Depends of ure
  Installing libutouch-grail1 as Depends of xserver-xorg-input-evdev
    Installing libmtdev1 as Depends of libutouch-grail1
  Installing libprotobuf6 as Depends of libcompizconfig0
  Installing compiz-core as Depends of libcompizconfig0
    previously satisfied important dependency on compiz-plugins
    Installing compiz-plugins as Recommends of compiz-core
  Installing update-manager-core as Depends of update-manager
  Installing openoffice.org-base-core as Depends of openoffice.org-writer
  Installing libqtassistantclient4 as Depends of libqt4-assistant
  Installing python-gconf as Depends of python-gnome2
  Installing libkde3support4 as Depends of k9copy
    Installing libkpty4 as Depends of libkde3support4
      Installing libutempter0 as Depends of libkpty4
    Installing libqt4-qt3support as Depends of libkde3support4
      Installing libqt4-designer as Depends of libqt4-qt3support
  Installing libkdesu5 as Depends of k9copy
  Installing gnome-media-common as Depends of gnome-media
  Installing nautilus-data as Depends of nautilus
  Installing gnome-games-common as Depends of aisleriot
  Installing libgnome2-common as Depends of libgnome2-0
  Installing libusb-1.0-0 as Depends of libdc1394-22
  Installing libbind9-60 as Depends of bind9-host
    Installing libdns66 as Depends of libbind9-60
      Installing libgeoip1 as Depends of libdns66
  Installing libisc60 as Depends of bind9-host
  Installing libisccfg60 as Depends of bind9-host
  Installing liblwres60 as Depends of bind9-host
  Installing openoffice.org-draw as Depends of openoffice.org-impress
  Installing language-pack-en as Depends of language-pack-en-base
  Installing gvfs as Depends of gvfs-fuse
  Installing erlang-base as Depends of erlang-inets
    previously satisfied important dependency on erlang-crypto
    Installing erlang-crypto as Recommends of erlang-base
    previously satisfied important dependency on erlang-syntax-tools
    Installing erlang-syntax-tools as Recommends of erlang-base
  Installing erlang-mnesia as Depends of erlang-inets
  Installing erlang-runtime-tools as Depends of erlang-inets
  Installing erlang-ssl as Depends of erlang-inets
    Installing erlang-public-key as Depends of erlang-ssl
  Installing python-markupsafe as Depends of python-mako
  Installing linux-headers-2.6.35-25-generic as Depends of linux-headers-generic
    Installing linux-headers-2.6.35-25 as Depends of linux-headers-2.6.35-25-generic
  Installing libaspell15 as Depends of aspell
  Installing dhcp3-common as Depends of dhcp3-client
  Installing gnucash-common as Depends of gnucash
  Installing libgoffice-0.8-8 as Depends of gnucash
    Installing libgsf-1-114 as Depends of libgoffice-0.8-8
      Installing libgsf-1-common as Depends of libgsf-1-114
    Installing libgoffice-0.8-8-common as Depends of libgoffice-0.8-8
  Installing libgtkhtml3.14-19 as Depends of gnucash
  Installing xsane-common as Depends of xsane
  Installing libtracker-client-0.8-0 as Depends of tracker
  Installing libtracker-miner-0.8-0 as Depends of tracker
  Installing libunac1 as Depends of tracker
  new important dependency: tracker-gui
  Installing tracker-gui as Recommends of tracker
    Installing libgee2 as Depends of tracker-gui
  new important dependency: tracker-miner-fs
  Installing tracker-miner-fs as Recommends of tracker
    Installing tracker-extract as Depends of tracker-miner-fs
      Installing libpoppler-glib5 as Depends of tracker-extract
        Installing libpoppler7 as Depends of libpoppler-glib5
      Installing libtotem-plparser17 as Depends of tracker-extract
      Installing libtracker-extract-0.8-0 as Depends of tracker-extract
  new important dependency: tracker-miner-evolution
  Installing tracker-miner-evolution as Recommends of tracker
    Installing libevolution as Depends of tracker-miner-evolution
      Installing libebackend1.2-0 as Depends of libevolution
      Installing libecal1.2-7 as Depends of libevolution
      Installing libedataserverui1.2-8 as Depends of libevolution
      Installing libgdata-google1.2-1 as Depends of libevolution
        Installing libgdata1.2-1 as Depends of libgdata-google1.2-1
      Installing libgtkhtml-editor0 as Depends of libevolution
        Installing libgtkhtml-editor-common as Depends of libgtkhtml-editor0
  Installing libdirectfb-1.2-9 as Depends of libxine1-x
  Installing libxine1-bin as Depends of libxine1-x
  Installing libsnmp-base as Depends of libsnmp15
  Installing libdjvulibre-text as Depends of libdjvulibre21
  Installing libmagickcore3 as Depends of obex-data-server
    Installing liblqr-1-0 as Depends of libmagickcore3
  Installing libmagickwand3 as Depends of obex-data-server
  Installing libdebconf-kde0 as Depends of kpackagekit
  Installing libpackagekit-qt-14 as Depends of kpackagekit
  Installing librasqal2 as Depends of librdf0
  Installing samba-common as Depends of smbclient
  Installing libnewt0.52 as Depends of whiptail
  Installing libvorbis0a as Depends of libvorbisfile3
  Installing plymouth as Depends of plymouth-x11
  Installing libgucharmap7 as Depends of gucharmap
  Installing libatspi1.0-0 as Depends of brltty-x11
  Installing brltty as Depends of brltty-x11
  Installing libevdocument3 as Depends of python-evince
    Installing libt1-5 as Depends of libevdocument3
  Installing libevview3 as Depends of python-evince
  Installing libnm-glib2 as Depends of network-manager
  Installing libnm-util1 as Depends of network-manager
  Installing libgirepository1.0-1 as Depends of libseed0
  Installing libmpfr4 as Depends of libseed0
  Installing libavahi-core7 as Depends of avahi-daemon
  Installing openjdk-6-jre as Depends of icedtea6-plugin
    Installing openjdk-6-jre-headless as Depends of openjdk-6-jre
      Installing openjdk-6-jre-lib as Depends of openjdk-6-jre-headless
      previously satisfied important dependency on icedtea-6-jre-cacao
      Installing icedtea-6-jre-cacao as Recommends of openjdk-6-jre-headless
  Installing gdebi-core as Depends of gdebi
    Installing python-apt as Depends of gdebi-core
      Installing apt-utils as Depends of python-apt
  Installing libimobiledevice1 as Depends of upower
  Installing libupower-glib1 as Depends of upower
  Installing libedata-book1.2-2 as Depends of evolution-exchange
  Installing libedata-cal1.2-7 as Depends of evolution-exchange
  Installing libegroupwise1.2-13 as Depends of evolution-exchange
  Installing evolution as Depends of evolution-exchange
    Installing evolution-data-server as Depends of evolution
      Installing evolution-data-server-common as Depends of evolution-data-server
  Installing libclutter-1.0-0 as Depends of quadrapassel
  Installing xul-ext-ubufox as Depends of ubufox
  Installing libpulse0 as Depends of pulseaudio
  Installing libgnome-bluetooth8 as Depends of gnome-bluetooth
  Installing python-aptdaemon as Depends of python-aptdaemon-gtk
  Installing libgladeui-1-9 as Depends of libgnome-media0
  Installing libwxbase2.8-0 as Depends of libwxgtk2.8-0
  Installing totem as Depends of totem-plugins
    Installing gstreamer0.10-plugins-base as Depends of totem
    Installing totem-common as Depends of totem
    previously satisfied important dependency on totem-mozilla
    Installing totem-mozilla as Recommends of totem
  Installing libgdata7 as Depends of totem-plugins
  Installing libkmediaplayer4 as Depends of kdebase-runtime
  Installing libknotifyconfig4 as Depends of kdebase-runtime
  Installing libnepomukquery4a as Depends of kdebase-runtime
  Installing kdebase-runtime-data as Depends of kdebase-runtime
  Installing plasma-scriptengine-javascript as Depends of kdebase-runtime
  new important dependency: virtuoso-minimal
  Installing virtuoso-minimal as Recommends of kdebase-runtime
    Installing virtuoso-opensource-6.1-bin as Depends of virtuoso-minimal
    Installing libvirtodbc0 as Depends of virtuoso-minimal
      Installing virtuoso-opensource-6.1-common as Depends of libvirtodbc0
  Installing linux-image-2.6.35-25-generic as Depends of linux-image-generic
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing libgssdp-1.0-2 as Depends of libgstfarsight0.10-0
  Installing libgupnp-1.0-3 as Depends of libgstfarsight0.10-0
  Installing libgupnp-igd-1.0-3 as Depends of libgstfarsight0.10-0
  Installing libx264-98 as Depends of gstreamer0.10-plugins-ugly-multiverse
  Installing libkunitconversion4 as Depends of plasma-widgets-workspace
  Installing libkworkspace4 as Depends of plasma-widgets-workspace
  Installing libplasmaclock4b as Depends of plasma-widgets-workspace
  Installing libmodplug1 as Depends of libxine1-misc-plugins
  Installing libmpcdec6 as Depends of libxine1-misc-plugins
  Installing libibus2 as Depends of ibus-gtk
  Installing libkimproxy4 as Depends of kdelibs5
  Installing libknewstuff2-4 as Depends of kdelibs5
  Installing python-gmenu as Depends of gnome-menus
  Installing libhpmud0 as Depends of hpijs
  Installing libprotoc6 as Depends of protobuf-compiler
  Installing libmysqlclient16 as Depends of mysql-client-core-5.1
    Installing mysql-common as Depends of libmysqlclient16
  Installing cups-common as Depends of cups-client
  Installing libavcodec52 as Depends of mplayer
    Installing libva1 as Depends of libavcodec52
    Installing libvpx0 as Depends of libavcodec52
  Installing libavformat52 as Depends of mplayer
  Installing libpostproc51 as Depends of mplayer
  Installing libvdpau1 as Depends of mplayer
  Installing language-pack-gnome-en as Depends of language-pack-gnome-en-base
  Installing libgnome-window-settings1 as Depends of gnome-control-center
  Installing capplets-data as Depends of gnome-control-center
  Installing libsasl2-2 as Depends of libsasl2-modules
  Installing libsane-hpaio as Depends of hplip
  Installing hplip-data as Depends of hplip
  new important dependency: python-sqlalchemy-ext
  Installing python-sqlalchemy-ext as Recommends of python-sqlalchemy
  Installing mono-csharp-shell as Depends of gbrainy
    Installing libmono-management2.0-cil as Depends of mono-csharp-shell
    Installing mono-gmcs as Depends of mono-csharp-shell
  Installing foomatic-db-compressed-ppds as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing ubuntu-extras-keyring as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: ibus-pinyin
  Installing ibus-pinyin as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing ibus-pinyin-db-open-phrase as Depends of ibus-pinyin
      Installing pinyin-database as Depends of ibus-pinyin-db-open-phrase
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
    Installing libgexiv2-0 as Depends of shotwell
  new important dependency: ttf-ubuntu-font-family
  Installing ttf-ubuntu-font-family as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  Installing libaccess-bridge-java as Depends of libaccess-bridge-java-jni
  Installing libboost-iostreams1.42.0 as Depends of aptitude
  Installing libept1 as Depends of aptitude
  Installing libfolks-telepathy0 as Depends of empathy
    Installing libfolks0 as Depends of libfolks-telepathy0
  Installing libtelepathy-logger1 as Depends of empathy
  Installing empathy-common as Depends of empathy
  Installing gnome-icon-theme as Depends of empathy
  Installing telepathy-logger as Depends of empathy
  Installing gtk2-engines-murrine as Depends of light-themes
  Installing libvte9 as Depends of vinagre
  Installing python-reportlab as Depends of python-reportlab-accel
  previously satisfied important dependency on scim-gtk2-immodule
  Installing scim-gtk2-immodule as Recommends of scim
  Installing odbcinst1debian2 as Depends of odbcinst
  Installing gir1.0-gdkpixbuf-2.0 as Depends of gir1.0-gtk-2.0
  Installing libbluetooth3 as Depends of bluez
  Installing libsyncdaemon-1.0-1 as Depends of ubuntuone-client-gnome
  Installing libgutenprint2 as Depends of cups-driver-gutenprint
  Installing gnome-terminal-data as Depends of gnome-terminal
  Installing e2fslibs as PreDepends of e2fsprogs
  Installing cpp-4.3 as Depends of gcc-4.3
  Installing gcc-4.4-base as Depends of gcc-4.4
  Installing cpp-4.4 as Depends of gcc-4.4
  Installing binutils as Depends of gcc-4.4
  Installing libgcc1 as Depends of gcc-4.4
  Installing mount as Depends of libfuse2
  Installing libaqbanking-data as Depends of libaqbanking29
  Installing baobab as Depends of gnome-utils
    Installing gnome-utils-common as Depends of baobab
  Installing gnome-dictionary as Depends of gnome-utils
  Installing gnome-screenshot as Depends of gnome-utils
  Installing gnome-search-tool as Depends of gnome-utils
  Installing gnome-system-log as Depends of gnome-utils
  Installing aptdaemon as Depends of software-center
  new important dependency: sessioninstaller
  Installing sessioninstaller as Recommends of software-center
  Installing python-sip as Depends of python-qt4
  Installing at-spi as Depends of python-pyatspi
  new important dependency: gpg
  Installing libbrasero-media1 as Depends of rhythmbox-plugin-cdrecorder
    Installing libburn4 as Depends of libbrasero-media1
    Installing libisofs6 as Depends of libbrasero-media1
  Installing kde-window-manager as Depends of kdebase-workspace-bin
    Installing libkdecorations4 as Depends of kde-window-manager
    Installing libkwineffects1a as Depends of kde-window-manager
  Installing libcln6 as Depends of kdebase-workspace-bin
  Installing libplasmagenericshell4 as Depends of kdebase-workspace-bin
  Installing libprocesscore4a as Depends of kdebase-workspace-bin
  Installing libprocessui4a as Depends of kdebase-workspace-bin
  Installing libqalculate5 as Depends of kdebase-workspace-bin
  Installing plasma-desktop as Depends of kdebase-workspace-bin
    Installing kdebase-workspace as Recommends of plasma-desktop
      Installing klipper as Depends of kdebase-workspace
      Installing ksysguard as Depends of kdebase-workspace
        Installing libksignalplotter4 as Depends of ksysguard
      Installing systemsettings as Depends of kdebase-workspace
      Installing kdm as Recommends of kdebase-workspace
        Installing kdebase-workspace-kgreet-plugins as Depends of kdm
      Installing kinfocenter as Recommends of kdebase-workspace
  Installing kdebase-workspace-data as Depends of kdebase-workspace-bin
    Installing oxygen-cursor-theme as Depends of kdebase-workspace-data
  Installing speech-dispatcher as Depends of python-speechd
  Installing python-gtk2 as Depends of python-glade2
  Installing usb-creator-common as Depends of usb-creator-gtk
  Installing language-selector-common as Depends of language-selector
  Installing tzdata as Depends of tzdata-java
  Installing libgwibber0 as Depends of indicator-me
  Installing libxapian15 as Depends of python-xapian
  Installing gir1.0-json-glib-1.0 as Depends of gir1.0-clutter-1.0
  Installing liblouis2 as Depends of python-louis
  Installing ubuntu-restricted-addons as Depends of ubuntu-restricted-extras
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing adobe-flashplugin as Recommends of ubuntu-restricted-addons
    Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing gstreamer0.10-fluendo-mp3 as Recommends of ubuntu-restricted-addons
    Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  Installing python-cups as Depends of system-config-printer-common
  Installing libbonobo2-common as Depends of libbonobo2-0
  Installing evince-common as Depends of evince
  Installing libmission-control-plugins0 as Depends of telepathy-mission-control-5
  Installing libcompress-raw-bzip2-perl as Depends of libio-compress-perl
  Installing libnetpbm10 as Depends of netpbm
  Installing libnice0 as Depends of telepathy-gabble
  Installing libstreams0 as Depends of libstreamanalyzer0
  Installing librtmp0 as Depends of gstreamer0.10-plugins-bad
  Installing libzbar0 as Depends of gstreamer0.10-plugins-bad
  Installing libsox1b as Depends of libsox-fmt-base
  Installing libdmapsharing2 as Depends of rhythmbox-plugins
  Installing libvala-0.10-0 as Depends of rhythmbox-plugins
  Installing libao4 as Depends of cdrdao
    Installing libao-common as Depends of libao4
  Installing libpackagekit-glib2-14 as Depends of packagekit
  Installing packagekit-backend-aptcc as Depends of packagekit
  previously satisfied important dependency on indicator-application
  Installing libgimp2.0 as Depends of gimp
    previously satisfied important dependency on gimp-data
    Installing gimp-data as Recommends of libgimp2.0
  Installing libakonadi-kabc4 as Depends of kdepimlibs5
  Installing libgpgme++2 as Depends of kdepimlibs5
  Installing libkblog4 as Depends of kdepimlibs5
    Installing libkxmlrpcclient4 as Depends of libkblog4
  Installing libkimap4 as Depends of kdepimlibs5
  Installing libkpimidentities4 as Depends of kdepimlibs5
    Installing libkpimtextedit4 as Depends of libkpimidentities4
  Installing libktnef4 as Depends of kdepimlibs5
  Installing libmailtransport4 as Depends of kdepimlibs5
  Installing libqgpgme1 as Depends of kdepimlibs5
  Installing kdepimlibs-kio-plugins as Depends of kdepimlibs5
  Installing gsfonts as Depends of ghostscript
  previously satisfied important dependency on ktorrent
  Installing ktorrent as Recommends of ktorrent-data
    Installing libktorrent2 as Depends of ktorrent
    Installing libktorrent-l10n as Depends of ktorrent
  Installing libestools2.0 as Depends of festival
  Installing alsa-oss as Depends of festival
  Installing oss-compat as Depends of festival
  Installing libalut0 as Depends of rss-glx
  Installing libglc0 as Depends of rss-glx
    Installing libglewmx1.5 as Depends of libglc0
  new important dependency: libmagickcore3-extra
  Installing libmagickcore3-extra as Recommends of imagemagick
    Installing libcdt4 as Depends of libmagickcore3-extra
    Installing libgraph4 as Depends of libmagickcore3-extra
    Installing libgvc5 as Depends of libmagickcore3-extra
      Installing libpathplan4 as Depends of libgvc5
      Installing libxdot4 as Depends of libgvc5
  Installing liboobs-1-5 as Depends of gnome-system-tools
  new important dependency: brasero-cdrkit
  Installing brasero-cdrkit as Recommends of brasero
  Installing python-papyon as Depends of telepathy-butterfly
  new important dependency: hwdata
  Installing hwdata as Recommends of libgnome-desktop-2-17
  Installing libboost-filesystem1.42.0 as Depends of mkvtoolnix
    Installing libboost-system1.42.0 as Depends of libboost-filesystem1.42.0
  Installing libboost-regex1.42.0 as Depends of mkvtoolnix
  Installing libebml2 as Depends of mkvtoolnix
  Installing libmatroska2 as Depends of mkvtoolnix
  Installing gnome-session-common as Depends of gnome-session
  Installing libntfs-3g79 as Depends of ntfs-3g
  Installing libgnomeprintui2.2-common as Depends of libgnomeprintui2.2-0
  new important dependency: usb-modeswitch
  Installing usb-modeswitch as Recommends of modemmanager
    Installing usb-modeswitch-data as Depends of usb-modeswitch
  Installing libmusicbrainz3-6 as Depends of sound-juicer
    Installing libdiscid0 as Depends of libmusicbrainz3-6
  new important dependency: python-gobject-cairo
  Installing python-gobject-cairo as Recommends of python-gobject
Starting
Starting 2
Investigating libc6
Package libc6 has broken Conflicts on libc6-i686
  Considering libc6-i686 -2 as a solution to libc6 14675
  Added libc6-i686 to the remove list
  Fixing libc6 via remove of libc6-i686
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating libesd0
Package libesd0 has broken Conflicts on libesd-alsa0
  Considering libesd-alsa0 -1 as a solution to libesd0 17
  Added libesd-alsa0 to the remove list
  Fixing libesd0 via remove of libesd-alsa0
Investigating libakonadi-kde4
Package libakonadi-kde4 has broken Conflicts on kdepimlibs-data
  Considering kdepimlibs-data -1 as a solution to libakonadi-kde4 13
  Added kdepimlibs-data to the remove list
  Fixing libakonadi-kde4 via remove of kdepimlibs-data
Investigating pm-utils
Package pm-utils has broken Conflicts on pm-utils-powersave-policy
  Considering pm-utils-powersave-policy -1 as a solution to pm-utils 10
  Added pm-utils-powersave-policy to the remove list
  Fixing pm-utils via remove of pm-utils-powersave-policy
Investigating libsolidcontrol4a
Package libsolidcontrol4a has broken Conflicts on libsolidcontrol4
  Considering libsolidcontrol4 -1 as a solution to libsolidcontrol4a 9
  Added libsolidcontrol4 to the remove list
  Fixing libsolidcontrol4a via remove of libsolidcontrol4
Investigating odbcinst1debian2
Package odbcinst1debian2 has broken Conflicts on odbcinst1debian1
  Considering odbcinst1debian1 -1 as a solution to odbcinst1debian2 6
  Added odbcinst1debian1 to the remove list
  Fixing odbcinst1debian2 via remove of odbcinst1debian1
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
Investigating libprocesscore4a
Package libprocesscore4a has broken Conflicts on libprocesscore4
  Considering libprocesscore4 1 as a solution to libprocesscore4a 4
  Added libprocesscore4 to the remove list
  Fixing libprocesscore4a via remove of libprocesscore4
Investigating libcdt4
Package libcdt4 has broken Conflicts on libgraphviz4
  Considering libgraphviz4 1 as a solution to libcdt4 3
  Added libgraphviz4 to the remove list
  Fixing libcdt4 via remove of libgraphviz4
Investigating libept0
Package libept0 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 29 as a solution to libept0 3
  Removing libept0 rather than change libapt-pkg-libc6.10-6-4.8
Investigating libtaskmanager4a
Package libtaskmanager4a has broken Conflicts on libtaskmanager4
  Considering libtaskmanager4 -1 as a solution to libtaskmanager4a 2
  Added libtaskmanager4 to the remove list
  Fixing libtaskmanager4a via remove of libtaskmanager4
 Try to Re-Instate xserver-xorg-video-tseng
Re-Instated xserver-xorg-video-tseng (12 vs 12)
Investigating libprocessui4a
Package libprocessui4a has broken Conflicts on libprocessui4
  Considering libprocessui4 -1 as a solution to libprocessui4a 2
  Added libprocessui4 to the remove list
  Fixing libprocessui4a via remove of libprocessui4
Investigating plasma-widgets-workspace
Package plasma-widgets-workspace has broken Conflicts on libplasma-applet-system-monitor4
  Considering libplasma-applet-system-monitor4 -1 as a solution to plasma-widgets-workspace 1
  Added libplasma-applet-system-monitor4 to the remove list
  Fixing plasma-widgets-workspace via remove of libplasma-applet-system-monitor4
Investigating libplasmaclock4b
Package libplasmaclock4b has broken Conflicts on libplasmaclock4
  Considering libplasmaclock4 -1 as a solution to libplasmaclock4b 1
  Added libplasmaclock4 to the remove list
  Fixing libplasmaclock4b via remove of libplasmaclock4
Investigating kdebase-workspace-bin
Package kdebase-workspace-bin has broken Conflicts on libkfontinst4
  Considering libkfontinst4 -1 as a solution to kdebase-workspace-bin 1
  Added libkfontinst4 to the remove list
  Fixing kdebase-workspace-bin via remove of libkfontinst4
Investigating libweather-ion4a
Package libweather-ion4a has broken Conflicts on libweather-ion4
  Considering libweather-ion4 -1 as a solution to libweather-ion4a 1
  Added libweather-ion4 to the remove list
  Fixing libweather-ion4a via remove of libweather-ion4
Investigating libbrasero-media0
Package libbrasero-media0 has broken Depends on brasero-common
  Considering brasero-common 16 as a solution to libbrasero-media0 -1
  Removing libbrasero-media0 rather than change brasero-common
Investigating libmagickcore2-extra
Package libmagickcore2-extra has broken Depends on libgraphviz4
  Considering libgraphviz4 1 as a solution to libmagickcore2-extra -1
  Removing libmagickcore2-extra rather than change libgraphviz4
Investigating usb-creator
Package usb-creator has broken Depends on usb-creator-gtk
  Considering usb-creator-gtk 3 as a solution to usb-creator -1
  Removing usb-creator rather than change usb-creator-gtk
Investigating libpackagekit-glib2-12
Package libpackagekit-glib2-12 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 29 as a solution to libpackagekit-glib2-12 -2
  Removing libpackagekit-glib2-12 rather than change libapt-pkg-libc6.10-6-4.8
Investigating libpackagekit-qt-12
Package libpackagekit-qt-12 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 29 as a solution to libpackagekit-qt-12 -2
  Removing libpackagekit-qt-12 rather than change libapt-pkg-libc6.10-6-4.8
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-video-all 5
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-video-all via keep of xserver-xorg-video-tseng
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 79 as a solution to xserver-xorg-video-all 5
  Removing xserver-xorg-video-all rather than change xserver-xorg-video-tseng
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 79 as a solution to xserver-xorg-core 79
  Holding Back xserver-xorg-core rather than change xserver-xorg-video-6
Investigating xserver-xorg
Package xserver-xorg has broken Depends on xserver-xorg-core
  Considering xserver-xorg-core 79 as a solution to xserver-xorg 48
  Holding Back xserver-xorg rather than change xserver-xorg-core
Investigating xserver-xorg-input-evdev
Package xserver-xorg-input-evdev has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-evdev 7
  Holding Back xserver-xorg-input-evdev rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-rendition
Package xserver-xorg-video-rendition has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-rendition 2
  Holding Back xserver-xorg-video-rendition rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3virge
Package xserver-xorg-video-s3virge has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-s3virge 2
  Holding Back xserver-xorg-video-s3virge rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-apm
Package xserver-xorg-video-apm has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-apm 2
  Holding Back xserver-xorg-video-apm rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ark
Package xserver-xorg-video-ark has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-ark 2
  Holding Back xserver-xorg-video-ark rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ati
Package xserver-xorg-video-ati has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-ati 2
  Holding Back xserver-xorg-video-ati rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-tdfx
Package xserver-xorg-video-tdfx has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-tdfx 2
  Holding Back xserver-xorg-video-tdfx rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-trident
Package xserver-xorg-video-trident has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-trident 2
  Holding Back xserver-xorg-video-trident rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-fbdev
Package xserver-xorg-video-fbdev has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-fbdev 2
  Holding Back xserver-xorg-video-fbdev rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-wacom
Package xserver-xorg-input-wacom has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-wacom 2
  Holding Back xserver-xorg-input-wacom rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-mga
Package xserver-xorg-video-mga has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-mga 2
  Holding Back xserver-xorg-video-mga rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-vmmouse
Package xserver-xorg-input-vmmouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-vmmouse 2
  Holding Back xserver-xorg-input-vmmouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-input-mouse
Package xserver-xorg-input-mouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-mouse 2
  Holding Back xserver-xorg-input-mouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-r128
Package xserver-xorg-video-r128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-r128 2
  Holding Back xserver-xorg-video-r128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-openchrome 2
  Holding Back xserver-xorg-video-openchrome rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vesa
Package xserver-xorg-video-vesa has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-vesa 2
  Holding Back xserver-xorg-video-vesa rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-siliconmotion
Package xserver-xorg-video-siliconmotion has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-siliconmotion 2
  Holding Back xserver-xorg-video-siliconmotion rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-mach64
Package xserver-xorg-video-mach64 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-mach64 2
  Holding Back xserver-xorg-video-mach64 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-sis
Package xserver-xorg-video-sis has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-sis 2
  Holding Back xserver-xorg-video-sis rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3
Package xserver-xorg-video-s3 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-s3 2
  Holding Back xserver-xorg-video-s3 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-nv
Package xserver-xorg-video-nv has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nv 2
  Holding Back xserver-xorg-video-nv rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-savage
Package xserver-xorg-video-savage has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-savage 2
  Holding Back xserver-xorg-video-savage rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vmware
Package xserver-xorg-video-vmware has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-vmware 2
  Holding Back xserver-xorg-video-vmware rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-i128
Package xserver-xorg-video-i128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-i128 2
  Holding Back xserver-xorg-video-i128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-neomagic
Package xserver-xorg-video-neomagic has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-neomagic 2
  Holding Back xserver-xorg-video-neomagic rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-chips
Package xserver-xorg-video-chips has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-chips 2
  Holding Back xserver-xorg-video-chips rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-voodoo
Package xserver-xorg-video-voodoo has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-voodoo 2
  Holding Back xserver-xorg-video-voodoo rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-i740
Package xserver-xorg-video-i740 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-i740 2
  Holding Back xserver-xorg-video-i740 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-synaptics
Package xserver-xorg-input-synaptics has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-synaptics 2
  Holding Back xserver-xorg-input-synaptics rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-sisusb
Package xserver-xorg-video-sisusb has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-sisusb 2
  Holding Back xserver-xorg-video-sisusb rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-radeon
Package xserver-xorg-video-radeon has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-radeon 2
  Holding Back xserver-xorg-video-radeon rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-cirrus
Package xserver-xorg-video-cirrus has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-cirrus 2
  Holding Back xserver-xorg-video-cirrus rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-intel
Package xserver-xorg-video-intel has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-intel 2
  Holding Back xserver-xorg-video-intel rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-v4l
Package xserver-xorg-video-v4l has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-v4l 0
  Holding Back xserver-xorg-video-v4l rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-core
 Try to Re-Instate xserver-xorg
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
 Try to Re-Instate xserver-xorg-input-evdev
 Try to Re-Instate xserver-xorg-video-rendition
 Try to Re-Instate xserver-xorg-video-s3virge
 Try to Re-Instate xserver-xorg-video-apm
 Try to Re-Instate xserver-xorg-video-ark
 Try to Re-Instate xserver-xorg-video-ati
 Try to Re-Instate xserver-xorg-video-tdfx
 Try to Re-Instate xserver-xorg-video-trident
 Try to Re-Instate xserver-xorg-video-fbdev
 Try to Re-Instate xserver-xorg-input-wacom
 Try to Re-Instate xserver-xorg-video-mga
 Try to Re-Instate xserver-xorg-input-vmmouse
 Try to Re-Instate xserver-xorg-input-mouse
 Try to Re-Instate xserver-xorg-video-r128
 Try to Re-Instate xserver-xorg-video-openchrome
 Try to Re-Instate xserver-xorg-video-vesa
 Try to Re-Instate xserver-xorg-video-siliconmotion
 Try to Re-Instate xserver-xorg-video-mach64
 Try to Re-Instate xserver-xorg-video-sis
 Try to Re-Instate xserver-xorg-video-s3
 Try to Re-Instate xserver-xorg-video-nv
 Try to Re-Instate xserver-xorg-video-savage
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-video-vmware
 Try to Re-Instate xserver-xorg-video-i128
 Try to Re-Instate xserver-xorg-video-neomagic
 Try to Re-Instate xserver-xorg-video-chips
 Try to Re-Instate xserver-xorg-video-voodoo
 Try to Re-Instate xserver-xorg-video-i740
 Try to Re-Instate xserver-xorg-input-synaptics
 Try to Re-Instate xserver-xorg-video-sisusb
 Try to Re-Instate xserver-xorg-video-radeon
 Try to Re-Instate xserver-xorg-video-cirrus
 Try to Re-Instate xserver-xorg-video-intel
 Try to Re-Instate xserver-xorg-video-v4l
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Done
```

and main.log

```
2011-02-23 11:56:53,341 INFO Using config files '['./DistUpgrade.cfg']'
2011-02-23 11:56:53,341 INFO uname information: 'Linux hafiz-desktop 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686'
2011-02-23 11:56:53,341 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/preferences.d/', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2011-02-23 11:56:53,554 INFO release-upgrader version '0.142.20' started
2011-02-23 11:56:53,757 DEBUG svg pixbuf loader failed (Error displaying image)
2011-02-23 11:56:53,845 DEBUG Using 'DistUpgradeViewGtk' view
2011-02-23 11:56:53,885 DEBUG aufsOptionsAndEnvironmentSetup()
2011-02-23 11:56:53,886 DEBUG using '/tmp/upgrade-rw-sViwZr' as aufs_rw_dir
2011-02-23 11:56:53,886 DEBUG using '/tmp/upgrade-chroot-BDHDme' as aufs chroot dir
2011-02-23 11:56:53,886 DEBUG enable dpkg --force-overwrite
2011-02-23 11:56:53,952 DEBUG lsb-release: 'lucid'
2011-02-23 11:56:53,958 DEBUG who -m --ips: ''
2011-02-23 11:56:53,959 DEBUG _pythonSymlinkCheck run
2011-02-23 11:56:53,959 DEBUG openCache()
2011-02-23 11:56:55,667 DEBUG /openCache(), new cache size 30532
2011-02-23 11:56:55,668 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-02-23 11:56:55,668 DEBUG checkViewDepends()
2011-02-23 11:56:55,668 DEBUG running doUpdate() (showErrors=False)
2011-02-23 11:57:00,318 DEBUG openCache()
2011-02-23 11:57:00,722 DEBUG /openCache(), new cache size 30532
2011-02-23 11:57:00,723 DEBUG doPostInitialUpdate
2011-02-23 11:57:00,723 DEBUG Plugin modules in ./plugins: kdelibs4to5_plugin.py dpkg_status_plugin.py deb_plugin.py remove_lilo_plugin.py langpack_manual_plugin.py
2011-02-23 11:57:00,723 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2011-02-23 11:57:00,724 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2011-02-23 11:57:00,725 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2011-02-23 11:57:00,726 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2011-02-23 11:57:00,727 DEBUG Loading module ./plugins/deb_plugin.py
2011-02-23 11:57:00,727 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2011-02-23 11:57:00,728 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2011-02-23 11:57:00,729 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2011-02-23 11:57:00,729 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2011-02-23 11:57:00,731 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2011-02-23 11:57:00,731 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2011-02-23 11:57:00,732 DEBUG plugins for condition 'maverickPostInitialUpdate' are '[]'
2011-02-23 11:57:00,732 DEBUG plugins for condition 'from_lucidPostInitialUpdate' are '[]'
2011-02-23 11:57:05,450 DEBUG Foreign: nautilus-dropbox
2011-02-23 11:57:05,450 DEBUG Obsolete: language-support-translations-en
2011-02-23 11:57:05,452 DEBUG updateSourcesList()
2011-02-23 11:57:05,539 DEBUG rewriteSourcesList()
2011-02-23 11:57:05,542 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted'
2011-02-23 11:57:05,543 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted' updated to new dist
2011-02-23 11:57:05,543 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted'
2011-02-23 11:57:05,543 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted' updated to new dist
2011-02-23 11:57:05,543 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted'
2011-02-23 11:57:05,543 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted' updated to new dist
2011-02-23 11:57:05,544 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted'
2011-02-23 11:57:05,544 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted' updated to new dist
2011-02-23 11:57:05,544 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe'
2011-02-23 11:57:05,544 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe' updated to new dist
2011-02-23 11:57:05,544 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe'
2011-02-23 11:57:05,544 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe' updated to new dist
2011-02-23 11:57:05,545 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe'
2011-02-23 11:57:05,545 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe' updated to new dist
2011-02-23 11:57:05,545 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe'
2011-02-23 11:57:05,545 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe' updated to new dist
2011-02-23 11:57:05,545 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse'
2011-02-23 11:57:05,545 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse' updated to new dist
2011-02-23 11:57:05,546 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse'
2011-02-23 11:57:05,546 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse' updated to new dist
2011-02-23 11:57:05,546 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse'
2011-02-23 11:57:05,546 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse' updated to new dist
2011-02-23 11:57:05,546 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse'
2011-02-23 11:57:05,546 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse' updated to new dist
2011-02-23 11:57:05,547 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted'
2011-02-23 11:57:05,547 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted' updated to new dist
2011-02-23 11:57:05,547 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted'
2011-02-23 11:57:05,547 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted' updated to new dist
2011-02-23 11:57:05,547 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe'
2011-02-23 11:57:05,547 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe' updated to new dist
2011-02-23 11:57:05,548 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe'
2011-02-23 11:57:05,548 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe' updated to new dist
2011-02-23 11:57:05,548 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse'
2011-02-23 11:57:05,548 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse' updated to new dist
2011-02-23 11:57:05,548 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse'
2011-02-23 11:57:05,548 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse' updated to new dist
2011-02-23 11:57:05,549 DEBUG examining: 'deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) lucid main'
2011-02-23 11:57:05,553 DEBUG entry '# deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-02-23 11:57:05,553 DEBUG examining: 'deb [http://ppa.launchpad.net/pellesimon/ppa/ubuntu](http://ppa.launchpad.net/pellesimon/ppa/ubuntu) lucid main'
2011-02-23 11:57:05,558 DEBUG entry '# deb [http://ppa.launchpad.net/pellesimon/ppa/ubuntu](http://ppa.launchpad.net/pellesimon/ppa/ubuntu) maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-02-23 11:57:05,558 DEBUG examining: 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner'
2011-02-23 11:57:05,558 DEBUG entry 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner' updated to new dist
2011-02-23 11:57:05,559 DEBUG examining: 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner'
2011-02-23 11:57:05,559 DEBUG entry 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner' updated to new dist
2011-02-23 11:57:07,637 DEBUG running doUpdate() (showErrors=True)
2011-02-23 11:57:11,803 DEBUG openCache()
2011-02-23 11:57:11,804 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-02-23 11:57:14,711 DEBUG /openCache(), new cache size 32494
2011-02-23 11:57:14,712 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
```

Where to now? Is the upgrade worth the trouble?

---

### Post by lou002 on 2011-02-23
I've had the same problem, opened a thread on here too. So far nothing that's been suggested work. It's frustrating too, because I want to upgrade to 10.10 so I can use 11.04.

---

### Post by An Sanct on 2011-02-24
11.04 is currently Alpha 2 and far from usable, my advice would be, if you want to test Natty now, use VirtualBox.

PS. To upgrade, you can download the "Alternative" version and upgrade from a CD, IMHO its better to download one ISO, burn it and decide when it is going to be installed, then to upgrade from the net and wait for it to download + install (not knowing how long it will take). Aborting upgrade means breaking something, my experience was really bad.

And I don't mean the upgrading or installation experience, I just couldn't do the whole upgrade in one piece and broke the system so badly, that I had to rescue files via live USB + external drive and finally had to installed a clean OS.

---

### Post by Insperatus on 2011-02-25
> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

I was having the same trouble (and my /var/log/dist-upgrade/apt.log looked similar), then I discovered this bug report:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652)

I ***found a solution by reading*** the comments, seems all one has to do is: ```
sudo apt-get remove xserver-xorg-video-nouveau
```

Many folks explained this solution worked for them, and it worked for me! After removing the problem package I upgraded via the command line:```
sudo do-release-upgrade -d
```

Using the GUI to upgrade probably works too I just wanted to use the CLI for fun (haha.) A few people suggested reinstalling the xserver package when everything's done. ```
sudo apt-get install xserver-xorg-video-nouveau
```

My upgrade is still in progress but things are going along smoothly, well past the annoying "unresolvable problem" interrupting. Let me know if you have any luck and if this works for you remember to mark the thread "solved"  :)

---

### Post by lou002 on 2011-02-25
> **Insperatus said:**
> I was having the same trouble (and my /var/log/dist-upgrade/apt.log looked similar), then I discovered this bug report:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652)

I ***found a solution by reading*** the comments, seems all one has to do is: ```
sudo apt-get remove xserver-xorg-video-nouveau
```

Many folks explained this solution worked for them, and it worked for me! After removing the problem package I upgraded via the command line:```
sudo do-release-upgrade -d
```

Using the GUI to upgrade probably works too I just wanted to use the CLI for fun (haha.) A few people suggested reinstalling the xserver package when everything's done. ```
sudo apt-get install xserver-xorg-video-nouveau
```

My upgrade is still in progress but things are going along smoothly, well past the annoying "unresolvable problem" interrupting. Let me know if you have any luck and if this works for you remember to mark the thread "solved"  :)


This helped me!:guitar:

---

### Post by hansolo4949 on 2011-02-25
Yes, I would wait for natty to be released ti start using it, and I know this has probably been suggested before, but try fixing any broken packages that occur. Another option would be to do it manually inside of synaptic, if there's a problem with the updater. Just my two cents:)

---

### Post by moth17 on 2011-03-01
> **An Sanct said:**
> PS. To upgrade, you can download the "Alternative" version and upgrade from a CD, IMHO its better to download one ISO, burn it and decide when it is going to be installed, then to upgrade from the net and wait for it to download + install (not knowing how long it will take). Aborting upgrade means breaking something, my experience was really bad.

And I don't mean the upgrading or installation experience, I just couldn't do the whole upgrade in one piece and broke the system so badly, that I had to rescue files via live USB + external drive and finally had to installed a clean OS.

Thanks, got past that hurtle. Now your quote freaked me out a little. I haven't done an upgrade from a disc. What's the procedure?

---

### Post by moth17 on 2011-03-03
I ran the update online. No problems as far as I can tell. Grazie Mille. 

\\:D/

---

