---
title: "Help, Unmet Dependencies"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by The Low End Theory on 2010-12-18
I can't install or uninstall anything, when i do sudo apt-get upgrade i get
```
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 desktop-file-utils : Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
 libc6 : Depends: libc-bin (= 2.12.1-0ubuntu10) but it is not installed
         Depends: libgcc1 but it is not installed
         Depends: tzdata but it is not installed
         Depends: findutils (>= 4.4.0-2ubuntu2) but it is not installed
 man-db : Depends: groff-base (>= 1.18.1.1-15) but it is not installed
          Depends: bsdmainutils but it is not installed
          Depends: debconf (>= 1.2.0) but it is not installed or
                   debconf-2.0
          Depends: dpkg (>= 1.9.0) but it is not installed
          Depends: libgdbm3 (>= 1.8.3) but it is not installed
          Depends: zlib1g (>= 1:1.1.4) but it is not installed
 python-gmenu : Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                Depends: libgnome-menu2 (>= 2.27.92) but it is not installed
                Depends: python (< 2.7) but it is not installed
                Depends: python (>= 2.6) but it is not installed
                Depends: python-support (>= 0.90.0) but it is not installed
                Depends: python-gtk2 but it is not installed
                Depends: python-xdg (>= 0.18-1ubuntu2) but it is not installed
E: Unmet dependencies. Try using -f.

```

sudo apt-get install -f returns

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  adduser apt apt-utils base-files base-passwd bsdmainutils bsdutils
  busybox-initramfs consolekit coreutils cpio cpp cpp-4.4 dbus debconf
  debconf-i18n debianutils defoma dpkg e2fslibs e2fsprogs file findutils
  fontconfig fontconfig-config gawk gcc-4.4-base gcc-4.5-base gir1.0-glib-2.0
  gpgv groff-base hicolor-icon-theme ifupdown initramfs-tools
  initramfs-tools-bin initscripts insserv klibc-utils libacl1 libatk1.0-0
  libatk1.0-data libattr1 libavahi-client3 libavahi-common-data
  libavahi-common3 libblkid1 libbz2-1.0 libc-bin libcairo2 libck-connector0
  libcomerr2 libcups2 libdatrie1 libdb4.8 libdbus-1-3 libdbus-glib-1-2
  libdconf0 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2
  libeggdbus-1-0 libexpat1 libffi5 libfontconfig1 libfontenc1 libfreetype6
  libfribidi0 libgcc1 libgcrypt11 libgdbm3 libgdk-pixbuf2.0-0
  libgirepository1.0-1 libglib2.0-0 libglib2.0-data libgmp3c2 libgnome-menu2
  libgnutls26 libgpg-error0 libgpm2 libgssapi-krb5-2 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libjasper1 libjpeg62 libk5crypto3 libkeyutils1 libklibc
  libkrb5-3 libkrb5support0 liblocale-gettext-perl liblzma2 libmagic1 libmpfr4
  libncurses5 libncursesw5 libnewt0.52 libnih-dbus1 libnih1
  libpam-ck-connector libpam-modules libpam-runtime libpam0g libpango1.0-0
  libpango1.0-common libpcre3 libpixman-1-0 libplymouth2 libpng12-0
  libpolkit-gobject-1-0 libpopt0 libreadline6 libselinux1 libsepol1 libslang2
  libsqlite3-0 libss2 libssl0.9.8 libstdc++6 libtasn1-3 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libthai-data libthai0 libtiff4
  libudev0 libusb-0.1-4 libuuid1 libx11-6 libx11-data libxau6 libxcb-render0
  libxcb-shm0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6
  libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 lsb-base make makedev mime-support module-init-tools mount
  mountall ncurses-bin net-tools netbase passwd perl perl-base perl-modules
  plymouth plymouth-theme-ubuntu-text procps psmisc python python-cairo
  python-gobject python-gobject-cairo python-gtk2 python-minimal
  python-support python-xdg python2.6 python2.6-minimal readline-common sed
  sensible-utils sgml-base shared-mime-info sysv-rc sysvinit-utils
  ttf-dejavu-core tzdata ubuntu-keyring ucf udev upstart util-linux
  uuid-runtime whiptail x-ttcidfont-conf x11-common xfonts-encodings
  xfonts-utils xml-core xz-utils zlib1g
Suggested packages:
  ecryptfs-utils aptitude synaptic wajig dpkg-dev apt-doc bzip2 lzma
  python-apt wamerican wordlist whois vacation cpp-doc gcc-4.4-locales
  dbus-x11 debconf-doc debconf-utils libterm-readline-gnu-perl libgnome2-perl
  libnet-ldap-perl defoma-doc psfontmgr dfontmgr libfont-freetype-perl gpart
  parted e2fsck-static mlocate locate slocate gnupg groff iproute dhcp3-client
  dhcp-client ppp bash-completion bootchart cups-common rng-tools gnutls-bin
  gpm krb5-doc krb5-user librsvg2-common gvfs libjasper-runtime libpam-doc
  ttf-japanese-gothic ttf-japanese-mincho ttf-thryomanes ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp make-doc nfs-common perl-doc python-doc python-tk
  python-profiler python-gobject-dbg python-gtk2-doc python-numpy
  python2.6-doc python2.6-profiler binutils binfmt-support sgml-base-doc
  sysv-rc-conf bum sash watershed util-linux-locales kbd console-tools
  dosfstools debhelper
Recommended packages:
  gpg
The following NEW packages will be installed:
  adduser apt apt-utils base-files base-passwd bsdmainutils bsdutils
  busybox-initramfs consolekit coreutils cpio cpp cpp-4.4 dbus debconf
  debconf-i18n debianutils defoma dpkg e2fslibs e2fsprogs file findutils
  fontconfig fontconfig-config gawk gcc-4.4-base gcc-4.5-base gir1.0-glib-2.0
  gpgv groff-base hicolor-icon-theme ifupdown initramfs-tools
  initramfs-tools-bin initscripts insserv klibc-utils libacl1 libatk1.0-0
  libatk1.0-data libattr1 libavahi-client3 libavahi-common-data
  libavahi-common3 libblkid1 libbz2-1.0 libc-bin libcairo2 libck-connector0
  libcomerr2 libcups2 libdatrie1 libdb4.8 libdbus-1-3 libdbus-glib-1-2
  libdconf0 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2
  libeggdbus-1-0 libexpat1 libffi5 libfontconfig1 libfontenc1 libfreetype6
  libfribidi0 libgcc1 libgcrypt11 libgdbm3 libgdk-pixbuf2.0-0
  libgirepository1.0-1 libglib2.0-0 libglib2.0-data libgmp3c2 libgnome-menu2
  libgnutls26 libgpg-error0 libgpm2 libgssapi-krb5-2 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libjasper1 libjpeg62 libk5crypto3 libkeyutils1 libklibc
  libkrb5-3 libkrb5support0 liblocale-gettext-perl liblzma2 libmagic1 libmpfr4
  libncurses5 libncursesw5 libnewt0.52 libnih-dbus1 libnih1
  libpam-ck-connector libpam-modules libpam-runtime libpam0g libpango1.0-0
  libpango1.0-common libpcre3 libpixman-1-0 libplymouth2 libpng12-0
  libpolkit-gobject-1-0 libpopt0 libreadline6 libselinux1 libsepol1 libslang2
  libsqlite3-0 libss2 libssl0.9.8 libstdc++6 libtasn1-3 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libthai-data libthai0 libtiff4
  libudev0 libusb-0.1-4 libuuid1 libx11-6 libx11-data libxau6 libxcb-render0
  libxcb-shm0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6
  libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 lsb-base make makedev mime-support module-init-tools mount
  mountall ncurses-bin net-tools netbase passwd perl perl-base perl-modules
  plymouth plymouth-theme-ubuntu-text procps psmisc python python-cairo
  python-gobject python-gobject-cairo python-gtk2 python-minimal
  python-support python-xdg python2.6 python2.6-minimal readline-common sed
  sensible-utils sgml-base shared-mime-info sysv-rc sysvinit-utils
  ttf-dejavu-core tzdata ubuntu-keyring ucf udev upstart util-linux
  uuid-runtime whiptail x-ttcidfont-conf x11-common xfonts-encodings
  xfonts-utils xml-core xz-utils zlib1g
0 upgraded, 200 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/56.8MB of archives.
After this operation, 196MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Could not perform immediate configuration on 'libbz2-1.0'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```

---

### Post by beew on 2010-12-18
Hmm... 

How did you get yourself into this mess? 

Looks like you have enabled some ppas  with conflicting versions for some dependencies. I will take a look at the sources list.

Go to the terminal and type ```
 gksudo gedit /etc/apt/sources.list
``` and post the content here so others can have a look.

---

### Post by karthick87 on 2010-12-18
post the output of,
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by The Low End Theory on 2010-12-18
well it started after my computer crashed while it was updating packages, the sources.list is empty.


sudo  apt-get install -f


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  adduser apt apt-utils base-files base-passwd bsdmainutils bsdutils
  busybox-initramfs consolekit coreutils cpio cpp cpp-4.4 dbus debconf
  debconf-i18n debianutils defoma dpkg e2fslibs e2fsprogs file findutils
  fontconfig fontconfig-config gawk gcc-4.4-base gcc-4.5-base gir1.0-glib-2.0
  gpgv groff-base hicolor-icon-theme ifupdown initramfs-tools
  initramfs-tools-bin initscripts insserv klibc-utils libacl1 libatk1.0-0
  libatk1.0-data libattr1 libavahi-client3 libavahi-common-data
  libavahi-common3 libblkid1 libbz2-1.0 libc-bin libcairo2 libck-connector0
  libcomerr2 libcups2 libdatrie1 libdb4.8 libdbus-1-3 libdbus-glib-1-2
  libdconf0 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2
  libeggdbus-1-0 libexpat1 libffi5 libfontconfig1 libfontenc1 libfreetype6
  libfribidi0 libgcc1 libgcrypt11 libgdbm3 libgdk-pixbuf2.0-0
  libgirepository1.0-1 libglib2.0-0 libglib2.0-data libgmp3c2 libgnome-menu2
  libgnutls26 libgpg-error0 libgpm2 libgssapi-krb5-2 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libjasper1 libjpeg62 libk5crypto3 libkeyutils1 libklibc
  libkrb5-3 libkrb5support0 liblocale-gettext-perl liblzma2 libmagic1 libmpfr4
  libncurses5 libncursesw5 libnewt0.52 libnih-dbus1 libnih1
  libpam-ck-connector libpam-modules libpam-runtime libpam0g libpango1.0-0
  libpango1.0-common libpcre3 libpixman-1-0 libplymouth2 libpng12-0
  libpolkit-gobject-1-0 libpopt0 libreadline6 libselinux1 libsepol1 libslang2
  libsqlite3-0 libss2 libssl0.9.8 libstdc++6 libtasn1-3 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libthai-data libthai0 libtiff4
  libudev0 libusb-0.1-4 libuuid1 libx11-6 libx11-data libxau6 libxcb-render0
  libxcb-shm0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6
  libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 lsb-base make makedev mime-support module-init-tools mount
  mountall ncurses-bin net-tools netbase passwd perl perl-base perl-modules
  plymouth plymouth-theme-ubuntu-text procps psmisc python python-cairo
  python-gobject python-gobject-cairo python-gtk2 python-minimal
  python-support python-xdg python2.6 python2.6-minimal readline-common sed
  sensible-utils sgml-base shared-mime-info sysv-rc sysvinit-utils
  ttf-dejavu-core tzdata ubuntu-keyring ucf udev upstart util-linux
  uuid-runtime whiptail x-ttcidfont-conf x11-common xfonts-encodings
  xfonts-utils xml-core xz-utils zlib1g
Suggested packages:
  ecryptfs-utils aptitude synaptic wajig dpkg-dev apt-doc bzip2 lzma
  python-apt wamerican wordlist whois vacation cpp-doc gcc-4.4-locales
  dbus-x11 debconf-doc debconf-utils libterm-readline-gnu-perl libgnome2-perl
  libnet-ldap-perl defoma-doc psfontmgr dfontmgr libfont-freetype-perl gpart
  parted e2fsck-static mlocate locate slocate gnupg groff iproute dhcp3-client
  dhcp-client ppp bash-completion bootchart cups-common rng-tools gnutls-bin
  gpm krb5-doc krb5-user librsvg2-common gvfs libjasper-runtime libpam-doc
  ttf-japanese-gothic ttf-japanese-mincho ttf-thryomanes ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp make-doc nfs-common perl-doc python-doc python-tk
  python-profiler python-gobject-dbg python-gtk2-doc python-numpy
  python2.6-doc python2.6-profiler binutils binfmt-support sgml-base-doc
  sysv-rc-conf bum sash watershed util-linux-locales kbd console-tools
  dosfstools debhelper
Recommended packages:
  gpg
The following NEW packages will be installed:
  adduser apt apt-utils base-files base-passwd bsdmainutils bsdutils
  busybox-initramfs consolekit coreutils cpio cpp cpp-4.4 dbus debconf
  debconf-i18n debianutils defoma dpkg e2fslibs e2fsprogs file findutils
  fontconfig fontconfig-config gawk gcc-4.4-base gcc-4.5-base gir1.0-glib-2.0
  gpgv groff-base hicolor-icon-theme ifupdown initramfs-tools
  initramfs-tools-bin initscripts insserv klibc-utils libacl1 libatk1.0-0
  libatk1.0-data libattr1 libavahi-client3 libavahi-common-data
  libavahi-common3 libblkid1 libbz2-1.0 libc-bin libcairo2 libck-connector0
  libcomerr2 libcups2 libdatrie1 libdb4.8 libdbus-1-3 libdbus-glib-1-2
  libdconf0 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2
  libeggdbus-1-0 libexpat1 libffi5 libfontconfig1 libfontenc1 libfreetype6
  libfribidi0 libgcc1 libgcrypt11 libgdbm3 libgdk-pixbuf2.0-0
  libgirepository1.0-1 libglib2.0-0 libglib2.0-data libgmp3c2 libgnome-menu2
  libgnutls26 libgpg-error0 libgpm2 libgssapi-krb5-2 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libjasper1 libjpeg62 libk5crypto3 libkeyutils1 libklibc
  libkrb5-3 libkrb5support0 liblocale-gettext-perl liblzma2 libmagic1 libmpfr4
  libncurses5 libncursesw5 libnewt0.52 libnih-dbus1 libnih1
  libpam-ck-connector libpam-modules libpam-runtime libpam0g libpango1.0-0
  libpango1.0-common libpcre3 libpixman-1-0 libplymouth2 libpng12-0
  libpolkit-gobject-1-0 libpopt0 libreadline6 libselinux1 libsepol1 libslang2
  libsqlite3-0 libss2 libssl0.9.8 libstdc++6 libtasn1-3 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libthai-data libthai0 libtiff4
  libudev0 libusb-0.1-4 libuuid1 libx11-6 libx11-data libxau6 libxcb-render0
  libxcb-shm0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6
  libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 lsb-base make makedev mime-support module-init-tools mount
  mountall ncurses-bin net-tools netbase passwd perl perl-base perl-modules
  plymouth plymouth-theme-ubuntu-text procps psmisc python python-cairo
  python-gobject python-gobject-cairo python-gtk2 python-minimal
  python-support python-xdg python2.6 python2.6-minimal readline-common sed
  sensible-utils sgml-base shared-mime-info sysv-rc sysvinit-utils
  ttf-dejavu-core tzdata ubuntu-keyring ucf udev upstart util-linux
  uuid-runtime whiptail x-ttcidfont-conf x11-common xfonts-encodings
  xfonts-utils xml-core xz-utils zlib1g
0 upgraded, 200 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/56.8MB of archives.
After this operation, 196MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Could not perform immediate configuration on 'libbz2-1.0'.Please see  man 5 apt.conf under APT::Immediate-Configure for details. (2)
```

sudo dpkg --configure -a


```
dpkg: dependency problems prevent configuration of man-db:
 man-db depends on groff-base (>= 1.18.1.1-15); however:
  Package groff-base is not installed.
 man-db depends on bsdmainutils; however:
  Package bsdmainutils is not installed.
 man-db depends on debconf (>= 1.2.0) | debconf-2.0; however:
  Package debconf is not installed.
  Package debconf-2.0 is not installed.
 man-db depends on dpkg (>= 1.9.0); however:
  Package dpkg is not installed.
 man-db depends on libgdbm3 (>= 1.8.3); however:
  Package libgdbm3 is not installed.
 man-db depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is not installed.
dpkg: error processing man-db (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on libc-bin (= 2.12.1-0ubuntu10); however:
  Package libc-bin is not installed.
 libc6 depends on libgcc1; however:
  Package libgcc1 is not installed.
 libc6 depends on tzdata; however:
  Package tzdata is not installed.
 libc6 depends on findutils (>= 4.4.0-2ubuntu2); however:
  Package findutils is not installed.
dpkg: error processing libc6 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 man-db
 libc6
```


sudo apt-get update && sudo apt-get upgrade


```
Hit http://linux.dropbox.com maverick Release.gpg
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US           
Hit http://linux.dropbox.com maverick Release                                  
Get:1 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Get:2 http://ppa.launchpad.net maverick Release [9,753B]                       
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:3 http://dl.google.com stable Release.gpg [197B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://linux.dropbox.com maverick/main i386 Packages                       
Get:4 http://dl.google.com stable Release [1,347B]                             
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Get:5 http://dl.google.com stable/main i386 Packages [1,076B]                  
Hit http://extras.ubuntu.com maverick/main Sources                             
Get:6 http://ppa.launchpad.net maverick/main Sources [2,262B]                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                    
Hit http://us.archive.ubuntu.com maverick-updates Release                      
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Get:7 http://ppa.launchpad.net maverick/main i386 Packages [7,421B]  
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Fetched 22.4kB in 1s (15.0kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 desktop-file-utils : Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
 libc6 : Depends: libc-bin (= 2.12.1-0ubuntu10) but it is not installed
         Depends: libgcc1 but it is not installed
         Depends: tzdata but it is not installed
         Depends: findutils (>= 4.4.0-2ubuntu2) but it is not installed
 man-db : Depends: groff-base (>= 1.18.1.1-15) but it is not installed
          Depends: bsdmainutils but it is not installed
          Depends: debconf (>= 1.2.0) but it is not installed or
                   debconf-2.0
          Depends: dpkg (>= 1.9.0) but it is not installed
          Depends: libgdbm3 (>= 1.8.3) but it is not installed
          Depends: zlib1g (>= 1:1.1.4) but it is not installed
 python-gmenu : Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                Depends: libgnome-menu2 (>= 2.27.92) but it is not installed
                Depends: python (< 2.7) but it is not installed
                Depends: python (>= 2.6) but it is not installed
                Depends: python-support (>= 0.90.0) but it is not installed
                Depends: python-gtk2 but it is not installed
                Depends: python-xdg (>= 0.18-1ubuntu2) but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by beew on 2010-12-18
Well if the sources list is empty of course you can't install anything. To reactivate the default sources open Synaptic package manager, go to Settings >  Repositories and check all the boxes for the Ubuntu repositories.

EDITED: I see dpkg is not installed??!!

---

### Post by The Low End Theory on 2010-12-18
there is no repositories tab in settings, what do i do about dpkg not being installed? is that bad?

---

### Post by beew on 2010-12-18
This is strange. I am not sure I know how to help. dpkg is the backend to apt-get, Synaptic, Software Center and everything you need to install software. It is the package installer to put it simply. If it is not installed then pretty much nothing would install (unless you install from source or get a tarball with a install script or a .bin installer). If I were in your situation I would do a fresh install of Ubuntu. Maybe others have better suggestions, but I can't think of any.

Which version of Ubuntu are you using by the way and how did you install it? You may want to get a different iso too, as it might have been corrupted from the get go.

---

### Post by sikander3786 on 2010-12-19
sources.list can't be empty (your apt-get update output tells that). I suspect you spelled it wrong while trying to open it.

Copy/paste these commands into your terminal and post the output here.

```
cat /etc/apt/sources.list
```

```
ls -l /etc/apt/sources.list.d
```

---

### Post by The Low End Theory on 2010-12-21
cat /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe

```


ls -l /etc/apt/sources.list.d

```
total 24
-rw-r--r-- 1 root root 136 2010-12-18 13:47 awn-testing-ppa-maverick.list
-rw-r--r-- 1 root root 136 2010-12-18 13:47 awn-testing-ppa-maverick.list.save
-rw-r--r-- 1 root root  50 2010-12-18 13:47 dropbox.list
-rw-r--r-- 1 root root  50 2010-12-18 13:47 dropbox.list.save
-rw-r--r-- 1 root root 176 2010-12-18 13:47 google-chrome.list
-rw-r--r-- 1 root root 176 2010-12-18 13:47 google-chrome.list.save
```

---

### Post by sikander3786 on 2010-12-21
```
sudo apt-get dist-upgrade
```

---

### Post by The Low End Theory on 2010-12-21
sudo apt-get dist-upgrade

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 desktop-file-utils : Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
 libc6 : Depends: libc-bin (= 2.12.1-0ubuntu10) but it is not installed
         Depends: libgcc1 but it is not installed
         Depends: tzdata but it is not installed
         Depends: findutils (>= 4.4.0-2ubuntu2) but it is not installed
 man-db : Depends: groff-base (>= 1.18.1.1-15) but it is not installed
          Depends: bsdmainutils but it is not installed
          Depends: debconf (>= 1.2.0) but it is not installed or
                   debconf-2.0
          Depends: dpkg (>= 1.9.0) but it is not installed
          Depends: libgdbm3 (>= 1.8.3) but it is not installed
          Depends: zlib1g (>= 1:1.1.4) but it is not installed
 python-gmenu : Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                Depends: libgnome-menu2 (>= 2.27.92) but it is not installed
                Depends: python (< 2.7) but it is not installed
                Depends: python (>= 2.6) but it is not installed
                Depends: python-support (>= 0.90.0) but it is not installed
                Depends: python-gtk2 but it is not installed
                Depends: python-xdg (>= 0.18-1ubuntu2) but it is not installed
E: Unmet dependencies. Try using -f.

```

using -f gives 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  adduser apt apt-utils base-files base-passwd bash bash-completion
  bsdmainutils bsdutils busybox-initramfs consolekit coreutils cpio cpp
  cpp-4.4 dash dbus debconf debconf-i18n debianutils defoma diffutils dpkg
  e2fslibs e2fsprogs file findutils fontconfig fontconfig-config gawk
  gcc-4.4-base gcc-4.5-base gir1.0-glib-2.0 gpgv grep groff-base gzip
  hicolor-icon-theme hostname ifupdown initramfs-tools initramfs-tools-bin
  initscripts insserv klibc-utils libacl1 libatk1.0-0 libatk1.0-data libattr1
  libavahi-client3 libavahi-common-data libavahi-common3 libblkid1 libbz2-1.0
  libc-bin libcairo2 libck-connector0 libcomerr2 libcups2 libdatrie1 libdb4.8
  libdbus-1-3 libdbus-glib-1-2 libdconf0 libdrm-intel1 libdrm-nouveau1
  libdrm-radeon1 libdrm2 libeggdbus-1-0 libexpat1 libffi5 libfontconfig1
  libfontenc1 libfreetype6 libfribidi0 libgcc1 libgcrypt11 libgdbm3
  libgdk-pixbuf2.0-0 libgirepository1.0-1 libglib2.0-0 libglib2.0-data
  libgmp3c2 libgnome-menu2 libgnutls26 libgpg-error0 libgpm2 libgssapi-krb5-2
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libjasper1 libjpeg62 libk5crypto3
  libkeyutils1 libklibc libkrb5-3 libkrb5support0 liblocale-gettext-perl
  liblzma2 libmagic1 libmpfr4 libncurses5 libncursesw5 libnewt0.52
  libnih-dbus1 libnih1 libpam-ck-connector libpam-modules libpam-runtime
  libpam0g libpango1.0-0 libpango1.0-common libpcre3 libpixman-1-0
  libplymouth2 libpng12-0 libpolkit-gobject-1-0 libpopt0 libreadline6
  libselinux1 libsepol1 libslang2 libsqlite3-0 libss2 libssl0.9.8 libstdc++6
  libtasn1-3 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl
  libthai-data libthai0 libtiff4 libudev0 libusb-0.1-4 libuuid1 libx11-6
  libx11-data libxau6 libxcb-render0 libxcb-shm0 libxcb1 libxcomposite1
  libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3 libxfont1 libxft2
  libxi6 libxinerama1 libxml2 libxrandr2 libxrender1 login lsb-base make
  makedev mime-support module-init-tools mount mountall ncurses-base
  ncurses-bin net-tools netbase passwd perl perl-base perl-modules plymouth
  plymouth-theme-ubuntu-text procps psmisc python python-cairo python-gobject
  python-gobject-cairo python-gtk2 python-minimal python-support python-xdg
  python2.6 python2.6-minimal readline-common sed sensible-utils sgml-base
  shared-mime-info sysv-rc sysvinit-utils tar ttf-dejavu-core tzdata
  ubuntu-keyring ucf udev upstart util-linux uuid-runtime whiptail
  x-ttcidfont-conf x11-common xfonts-encodings xfonts-utils xml-core xz-utils
  zlib1g
0 upgraded, 210 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 4,992kB/59.1MB of archives.
After this operation, 205MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main dash i386 0.5.5.1-7ubuntu1 [96.3kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/main bash i386 4.1-2ubuntu4 [640kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ maverick/main diffutils i386 1:3.0-1 [146kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main libudev0 i386 162-2.2 [126kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main libglib2.0-0 i386 2.26.1-0ubuntu1 [1,381kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main udev i386 162-2.2 [428kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ maverick/main grep i386 2.6.3-3 [221kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ maverick/main gzip i386 1.3.12-9ubuntu1.1 [102kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ maverick/main hostname i386 3.04ubuntu1 [15.9kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ maverick/main login i386 1:4.1.4.2-1ubuntu3 [315kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ maverick/main tar i386 1.23-2 [403kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ maverick/main ncurses-base all 5.7+20100626-0ubuntu1 [190kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main libsqlite3-0 i386 3.7.2-1ubuntu0.1 [381kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ maverick/main bash-completion all 1:1.2-2ubuntu1 [138kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main libglib2.0-data all 2.26.1-0ubuntu1 [976B]
Get:16 http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main libpango1.0-common all 1.28.2-0ubuntu1 [114kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main libpango1.0-0 i386 1.28.2-0ubuntu1 [293kB]
Fetched 4,992kB in 8s (619kB/s)                                                
E: Could not perform immediate configuration on 'libbz2-1.0'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```

---

### Post by sikander3786 on 2010-12-21
Try,

```
sudo apt-get install libc-bin libgcc1 tzdata findutils groff-base bsdmainutils debconf dpkg libgdbm3 zlib1g libglib2.0-0 libgnome-menu2 python python-support python-gtk2 python-xdg
```

Or,

```
sudo apt-get install --reinstall libc-bin libgcc1 tzdata findutils groff-base bsdmainutils debconf dpkg libgdbm3 zlib1g libglib2.0-0 libgnome-menu2 python python-support python-gtk2 python-xdg
```

---

### Post by The Low End Theory on 2010-12-21
Both tell me E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by sikander3786 on 2010-12-21
Feeling stumped at this one...

Aptitude is not installed on Maverick by default but it is actually better at dealing with dependency problems than apt-get. If you installed it previously, you can try,

```
sudo aptitude install -f
```

And if aptitude isn't there, I am out of suggestions. Wait for some other mate to jump in with a better suggestion.

---

### Post by The Low End Theory on 2010-12-21
Hmm... well that didn't work, but thanks for all the help, i think if no one else comes along here soon, ill probably just reinstall.

---

### Post by Dr Widdleguy on 2012-03-13
Having the same exact problem as you Mr. Popo. I've tried everything they've suggested on here as well but to no avail. 

(Sorry for the reply on a 2 year old post.)

---

### Post by oldos2er on 2012-03-13
Closed, necromancy.

---

