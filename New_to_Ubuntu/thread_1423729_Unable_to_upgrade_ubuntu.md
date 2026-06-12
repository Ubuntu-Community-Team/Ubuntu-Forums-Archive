---
title: "Unable to upgrade ubuntu"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by navaneethan on 2010-03-07
> yeksram@yeksram-lap:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgtk2-sexy-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  base-files exiv2 grub kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5
  kdelibs5-data libass3 libavcodec52 libavformat52 libavutil49 libcddb2
  libdvbpsi5 libdvdnav4 libdvdread4 libexiv2-5 libgsm1 libgtk2-sexy-perl
  libice-dev libknotificationitem1 liblzma0 libmediastreamer0 libortp8
  libpam-modules libpam-runtime libpam0g libplasma3 libpostproc51 libpq5
  libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-gui
  libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-script
  libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml
  libqtcore4 libqtgui4 libquicktime1 libraptor1 librdf0 libschroedinger-1.0-0
  libsm-dev libsoprano4 libstreamanalyzer0 libstreams0 libswscale0
  libuniconf4.6 libupnp3 libvlc2 libvlccore2 libwvstreams4.6-base
  libwvstreams4.6-extras libx11-dev libx264-67 libxau-dev libxcb-keysyms1
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1-dev libxext-dev libxi-dev
  libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x
  libxml-namespacesupport-perl libxml-sax-expat-perl libxml-sax-perl
  libxml-simple-perl mysql-common openoffice.org-base-core openoffice.org-calc
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-math
  openoffice.org-writer python-compizconfig python-evolution
  python-gtkmozembed python-pysqlite2 python-uno python-wnck qt4-qtconfig
  raptor-utils samba-common screenlets smbclient soprano-daemon ttf-dejavu
  ttf-dejavu-extra vlc vlc-data vlc-nox vlc-plugin-pulse winbind wvdial
  x11proto-input-dev
Suggested packages:
  grub-doc mdadm djvulibre-bin libdvdcss2 debhelper fakeroot build-essential
  libpam-doc libqt4-dev gxine xine-ui libxine1-doc libxine-doc libxine1-ffmpeg
  openoffice.org-base openoffice.org-evolution openoffice.org-gcj
  openoffice.org-filter-binfilter default-jre gcj-jre java-gcj-compat
  openjdk-6-jre sun-java5-jre sun-java6-jre java5-runtime jre
  openoffice.org-java-common python-pysqlite2-doc python-pysqlite2-dbg xfconf
  smbfs videolan-doc
The following packages will be REMOVED:
  grub-pc gstreamer0.10-ffmpeg libavcodec51 libxcb-xlib0-dev vlc-alsa
The following NEW packages will be installed:
  exiv2 grub libass3 libavcodec52 libcddb2 libdvbpsi5 libdvdread4 libexiv2-5
  libgtk2-sexy-perl libknotificationitem1 liblzma0 libortp8 libplasma3
  libqt4-phonon libschroedinger-1.0-0 libuniconf4.6 libupnp3 libvlccore2
  libwvstreams4.6-base libwvstreams4.6-extras libx11-dev libx264-67
  libxcb-keysyms1 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin
  libxine1-console libxine1-misc-plugins libxine1-x
  libxml-namespacesupport-perl libxml-sax-expat-perl libxml-sax-perl
  libxml-simple-perl python-evolution python-gtkmozembed python-wnck
  ttf-dejavu ttf-dejavu-extra vlc-plugin-pulse wvdial
The following packages will be upgraded:
  base-files kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data
  kdebase-runtime-data-common kdelibs-bin kdelibs5 kdelibs5-data libavformat52
  libavutil49 libdvdnav4 libgsm1 libice-dev libmediastreamer0 libpam-modules
  libpam-runtime libpam0g libpostproc51 libpq5 libqt4-assistant libqt4-core
  libqt4-dbus libqt4-designer libqt4-gui libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-test libqt4-webkit libqt4-xml libqtcore4 libqtgui4 libquicktime1
  libraptor1 librdf0 libsm-dev libsoprano4 libstreamanalyzer0 libstreams0
  libswscale0 libvlc2 libxau-dev libxcb1-dev libxext-dev libxi-dev
  mysql-common openoffice.org-base-core openoffice.org-calc
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-math
  openoffice.org-writer python-compizconfig python-pysqlite2 python-uno
  qt4-qtconfig raptor-utils samba-common screenlets smbclient soprano-daemon
  vlc vlc-data vlc-nox winbind x11proto-input-dev
73 upgraded, 42 newly installed, 5 to remove and 280 not upgraded.
42 not fully installed or removed.
Need to get 60.0MB/122MB of archives.
After this operation, 56.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libice-dev 2:1.0.5-1 [61.9kB]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libsm-dev 2:1.1.0-2 [25.7kB]    
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxau-dev 1:1.0.4-2 [16.7kB]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main x11proto-input-dev 1.5.0-2ubuntu1 [12.1kB]
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxcb1-dev 1.4-1 [78.8kB]
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libx11-dev 2:1.2.2-1ubuntu1 [1,920kB]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxext-dev 2:1.0.99.1-0ubuntu4   
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxi-dev 2:1.2.1-2ubuntu1        
  Error reading from server - read (104: Connection reset by peer)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxml-namespacesupport-perl 1.09-3
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxml-sax-perl 0.96+dfsg-1       
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxml-sax-expat-perl 0.40-1      
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libwvstreams4.6-base 4.6-2        
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main base-files 5.0.0ubuntu7           
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libpam0g 1.1.0-2ubuntu1           
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libpam-modules 1.1.0-2ubuntu1     
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libpam-runtime 1.1.0-2ubuntu1     
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libwvstreams4.6-extras 4.6-2      
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libuniconf4.6 4.6-2               
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main wvdial 1.60.1+nmu2ubuntu1         
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libavutil49 4:0.5+svn20090706-2ubuntu2
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libgsm1 1.0.13-1                  
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libschroedinger-1.0-0 1.0.8-2     
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libavcodec52 4:0.5+svn20090706-2ubuntu2
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libswscale0 4:0.5+svn20090706-2ubuntu2
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe libquicktime1 2:1.1.1+debian-1build1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libknotificationitem1 4:4.3.2-0ubuntu1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxine1-bin 1.1.16.3-0ubuntu4    
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxine1-misc-plugins 1.1.16.3-0ubuntu4
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxcb-shape0 1.4-1               
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxcb-shm0 1.4-1                 
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxcb-xv0 1.4-1                  
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxine1-x 1.1.16.3-0ubuntu4      
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxine1-console 1.1.16.3-0ubuntu4
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxine1 1.1.16.3-0ubuntu4        
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe libortp8 3.1.2-2ubuntu2       
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe libmediastreamer0 3.1.2-2ubuntu2
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main grub 0.97-29ubuntu59              
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe python-pysqlite2 2.5.5-1ubuntu1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main raptor-utils 1.4.19-1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe libass3 0.9.6-1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libavformat52 4:0.5+svn20090706-2ubuntu2
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe vlc 1.0.2-1ubuntu2.1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe vlc-nox 1.0.2-1ubuntu2.1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe libcddb2 1.2.1-1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe libdvdread4 4.1.3-5ubuntu2
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe libdvdnav4 4.1.3-3
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libpostproc51 4:0.5+svn20090706-2ubuntu2
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe libupnp3 1:1.6.6-3
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe vlc-data 1.0.2-1ubuntu2.1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe libvlccore2 1.0.2-1ubuntu2.1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe libvlc2 1.0.2-1ubuntu2.1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe libx264-67 1:0.svn20090621+git364d7d-0ubuntu2
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main libxcb-keysyms1 0.3.6-1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe python-compizconfig 0.8.2-0ubuntu1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main python-wnck 2.28.0-0ubuntu1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe screenlets 0.1.2-7
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main exiv2 0.18.2-1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe libgtk2-sexy-perl 0.04-1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main openoffice.org-base-core 1:3.1.1-5ubuntu1.1
  403  Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main openoffice.org-base-core 1:3.1.1-5ubuntu1.1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main openoffice.org-core 1:3.1.1-5ubuntu1.1
  403  Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main openoffice.org-core 1:3.1.1-5ubuntu1.1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main python-evolution 2.28.0-0ubuntu1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main python-gtkmozembed 2.25.3-3ubuntu1
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main ttf-dejavu-extra 2.29-2
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main ttf-dejavu 2.29-2
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe vlc-plugin-pulse 1.0.2-1ubuntu2.1
  403  Forbidden
Fetched 2,115kB in 60s (34.9kB/s)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxext/libxext-dev_1.0.99.1-0ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxext/libxext-dev_1.0.99.1-0ubuntu4_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxi/libxi-dev_1.2.1-2ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxi/libxi-dev_1.2.1-2ubuntu1_i386.deb)  Error reading from server - read (104: Connection reset by peer)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxml-namespacesupport-perl/libxml-namespacesupport-perl_1.09-3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxml-namespacesupport-perl/libxml-namespacesupport-perl_1.09-3_all.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxml-sax-perl/libxml-sax-perl_0.96+dfsg-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxml-sax-perl/libxml-sax-perl_0.96+dfsg-1_all.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxml-sax-expat-perl/libxml-sax-expat-perl_0.40-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxml-sax-expat-perl/libxml-sax-expat-perl_0.40-1_all.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-base_4.6-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-base_4.6-2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_5.0.0ubuntu7_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_5.0.0ubuntu7_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.0-2ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.0-2ubuntu1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.0-2ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.0-2ubuntu1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.0-2ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.0-2ubuntu1_all.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-extras_4.6-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-extras_4.6-2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.6_4.6-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.6_4.6-2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.60.1+nmu2ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.60.1+nmu2ubuntu1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil49_0.5+svn20090706-2ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil49_0.5+svn20090706-2ubuntu2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.13-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.13-1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/schroedinger/libschroedinger-1.0-0_1.0.8-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/schroedinger/libschroedinger-1.0-0_1.0.8-2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec52_0.5+svn20090706-2ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec52_0.5+svn20090706-2ubuntu2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libswscale0_0.5+svn20090706-2ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libswscale0_0.5+svn20090706-2ubuntu2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.1.1+debian-1build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.1.1+debian-1build1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs-experimental/libknotificationitem1_4.3.2-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs-experimental/libknotificationitem1_4.3.2-0ubuntu1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.16.3-0ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.16.3-0ubuntu4_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-misc-plugins_1.1.16.3-0ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-misc-plugins_1.1.16.3-0ubuntu4_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0_1.4-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shape0_1.4-1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shm0_1.4-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-shm0_1.4-1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xv0_1.4-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-xv0_1.4-1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.16.3-0ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.16.3-0ubuntu4_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.16.3-0ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.16.3-0ubuntu4_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.16.3-0ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.16.3-0ubuntu4_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/l/linphone/libortp8_3.1.2-2ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/l/linphone/libortp8_3.1.2-2ubuntu2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/l/linphone/libmediastreamer0_3.1.2-2ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/l/linphone/libmediastreamer0_3.1.2-2ubuntu2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu59_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu59_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/python-pysqlite2/python-pysqlite2_2.5.5-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/python-pysqlite2/python-pysqlite2_2.5.5-1ubuntu1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/r/raptor/raptor-utils_1.4.19-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/r/raptor/raptor-utils_1.4.19-1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/liba/libass/libass3_0.9.6-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/liba/libass/libass3_0.9.6-1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat52_0.5+svn20090706-2ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat52_0.5+svn20090706-2ubuntu2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_1.0.2-1ubuntu2.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_1.0.2-1ubuntu2.1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_1.0.2-1ubuntu2.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_1.0.2-1ubuntu2.1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libc/libcddb/libcddb2_1.2.1-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libc/libcddb/libcddb2_1.2.1-1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread4_4.1.3-5ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread4_4.1.3-5ubuntu2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdnav/libdvdnav4_4.1.3-3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdnav/libdvdnav4_4.1.3-3_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc51_0.5+svn20090706-2ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc51_0.5+svn20090706-2ubuntu2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libu/libupnp/libupnp3_1.6.6-3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libu/libupnp/libupnp3_1.6.6-3_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-data_1.0.2-1ubuntu2.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-data_1.0.2-1ubuntu2.1_all.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlccore2_1.0.2-1ubuntu2.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlccore2_1.0.2-1ubuntu2.1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc2_1.0.2-1ubuntu2.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc2_1.0.2-1ubuntu2.1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/x/x264/libx264-67_0.svn20090621+git364d7d-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/x/x264/libx264-67_0.svn20090621+git364d7d-0ubuntu2_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xcb-util/libxcb-keysyms1_0.3.6-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xcb-util/libxcb-keysyms1_0.3.6-1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/c/compizconfig-python/python-compizconfig_0.8.2-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/c/compizconfig-python/python-compizconfig_0.8.2-0ubuntu1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-python-desktop/python-wnck_2.28.0-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-python-desktop/python-wnck_2.28.0-0ubuntu1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/screenlets/screenlets_0.1.2-7_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/screenlets/screenlets_0.1.2-7_all.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/exiv2/exiv2_0.18.2-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/exiv2/exiv2_0.18.2-1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libg/libgtk2-sexy-perl/libgtk2-sexy-perl_0.04-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libg/libgtk2-sexy-perl/libgtk2-sexy-perl_0.04-1_i386.deb)  403  Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base-core_3.1.1-5ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base-core_3.1.1-5ubuntu1.1_i386.deb)  403  Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.1.1-5ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.1.1-5ubuntu1.1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-python-desktop/python-evolution_2.28.0-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-python-desktop/python-evolution_2.28.0-0ubuntu1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-python-extras/python-gtkmozembed_2.25.3-3ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-python-extras/python-gtkmozembed_2.25.3-3ubuntu1_i386.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.29-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.29-2_all.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu_2.29-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu_2.29-2_all.deb)  403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-pulse_1.0.2-1ubuntu2.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-pulse_1.0.2-1ubuntu2.1_i386.deb)  403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


I given this command to upgrade ubuntu for installing erlang but it was not successful...what is the reason ??? How to solve it?How to upgrade??
I wanna to install erlang..in this 9.04 ubuntu

---

### Post by Barriehie on 2010-03-07
The lines beginning with Err aren't complete url's for retrieval and the Failed to fetch lines are working via my browser!  Have you tried again since that attempt?  Could've been a server hiccup, if not post your sources.lst file.

---

### Post by skymera on 2010-03-07
Go to 

System > Administration > Software Sources

Click the "Download From"

Choose a new server and try again

---

