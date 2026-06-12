---
title: "Cannot install git-core"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by dethmaShine on 2010-08-24
EDIT: I am using ubuntu 9.10

I am trying to issue the following command using root:

[COLOR=DeepSkyBlue]apt-get install git-core
[/COLOR]
Error:
[COLOR=Red]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package git-core

[/COLOR]I need to use git to follow some other tutorial.

Any help?

Thanks!

EDIT: I have searched the forums but couldn't get the desired answer (OR the answer wasn't specific to my problem)

---

### Post by Joeb454 on 2010-08-24
Try running ```
apt-cache search git | less
```
This will list any application matching the search term of 'git', and pipe the output through less (as I imagine there will be a fair few that match it).

This should allow you to find the package you need

---

### Post by dethmaShine on 2010-08-24
> **Joeb454 said:**
> Try running ```
apt-cache search git | less
```This will list any application matching the search term of 'git', and pipe the output through less (as I imagine there will be a fair few that match it).

This should allow you to find the package you need

Thanks for the reply!

Following is the result:

esound-common - Enlightened Sound Daemon - Common files
libfreetype6 - FreeType 2 font engine, shared library files
libxmuu1 - X11 miscellaneous micro-utility library
libesd-alsa0 - Enlightened Sound Daemon (ALSA) - Shared libraries
libexif12 - library to parse EXIF files
libavc1394-0 - control IEEE 1394 audio/video devices
seahorse - GNOME front end for GnuPG
modemmanager - D-Bus service for managing modems
libmtp8 - Media Transfer Protocol (MTP) library
libxres1 - X11 Resource extension library
libxrender1 - X Rendering Extension client library
libxfont1 - X11 font rasterisation library
libxpm4 - X11 pixmap library
totem - A simple media player for the GNOME desktop based on GStreamer
libxrandr2 - X11 RandR extension library
libxcomposite1 - X11 Composite extension library
libdv4 - software library for DV format digital video (runtime lib)
libcdio-cdda0 - library to read and control digital audio CDs
libxi6 - X11 Input extension library
libcdio-paranoia0 - library to read digital audio CDs with error correction
gnupg - GNU privacy guard - a free PGP replacement
libcryptui0 - the UI library for DBUS functions exported by seahorse
libxfixes3 - X11 miscellaneous 'fixes' extension library
libfs6 - X11 Font Services library
libxmu6 - X11 miscellaneous utility library
libxdamage1 - X11 damaged region extension library
libxaw7 - X11 Athena Widget library
libx11-6 - X11 client-side library
ubuntu-keyring - GnuPG keys of the Ubuntu archive
eject - ejects CDs and operates CD-Changers under Linux
libxp6 - X Printing Extension (Xprint) client library
libgphoto2-2 - gphoto2 digital camera library
f-spot - personal photo management application
dcraw - decode raw digital camera images
libice6 - X11 Inter-Client Exchange library
libx11-data - X11 client-side library
libsm6 - X11 Session Management library
libxxf86vm1 - X11 XFree86 video mode extension library
libmusicbrainz4c2a - Second generation incarnation of the CD Index - library
libgphoto2-port0 - gphoto2 digital camera port library
libxau6 - X11 authorisation library

What am I supposed to do with these? Sorry I'm not that good with linux.

---

### Post by dethmaShine on 2010-08-24
Also, I am using ubuntu on VirtualBox and I'm on a proxy (if that helps).

---

### Post by Joeb454 on 2010-08-24
Hmm, that's odd. What repositories do you have enabled? You should be able to check by going to 'System > Administration > Software Sources' and checking in there.

---

### Post by dethmaShine on 2010-08-24
When I try to find any git files/packages:

root@kt-linux:/# find . -name "*git*"
./usr/src/linux-headers-2.6.31-14-generic/include/config/hid/logitech.h
./usr/src/linux-headers-2.6.31-14-generic/include/config/dvb/usb/digitv.h
./usr/src/linux-headers-2.6.31-14-generic/include/config/logitech
./usr/src/linux-headers-2.6.31-14/arch/sh/include/asm/.gitignore
./usr/src/linux-headers-2.6.31-14/scripts/kconfig/lxdialog/.gitignore
./usr/src/linux-headers-2.6.31-14/scripts/kconfig/.gitignore
./usr/src/linux-headers-2.6.31-14/scripts/mod/.gitignore
./usr/src/linux-headers-2.6.31-14/scripts/genksyms/.gitignore
./usr/src/linux-headers-2.6.31-14/scripts/basic/.gitignore
./usr/src/linux-headers-2.6.31-14/scripts/dtc/.gitignore
./usr/src/linux-headers-2.6.31-14/scripts/.gitignore
./usr/src/linux-headers-2.6.31-14/scripts/selinux/mdp/.gitignore
./usr/share/app-install/desktop/qgit.desktop
./usr/share/app-install/desktop/flegita.desktop
./usr/share/app-install/desktop/gitg.desktop
./usr/share/app-install/icons/flegita.svg
./usr/share/app-install/icons/_usr_share_git-cola_icons_git.svg
./usr/share/app-install/icons/gitg48x48.png
./usr/share/media-player-info/jetflash-digital_live250.mpi
./usr/share/fonts/truetype/ttf-kacst/KacstDigital.ttf
./usr/share/ca-certificates/mozilla/Digital_Signature_Trust_Co._Global_CA_4.crt
./usr/share/ca-certificates/mozilla/Digital_Signature_Trust_Co._Global_CA_3.crt
./usr/share/ca-certificates/mozilla/Digital_Signature_Trust_Co._Global_CA_2.crt
./usr/share/ca-certificates/mozilla/Digital_Signature_Trust_Co._Global_CA_1.crt
./usr/share/perl/5.10.0/unicore/To/Digit.pl
./usr/share/perl/5.10.0/unicore/lib/gc_sc/Digit.pl
./usr/share/perl/5.10.0/unicore/lib/gc_sc/HexDigit.pl
./usr/share/perl/5.10.0/unicore/lib/gc_sc/XDigit.pl
./usr/share/doc/rsync/scripts/git-set-file-times.gz
./usr/share/X11/xkb/keymap/digital_vndr
./usr/share/X11/xkb/keycodes/digital_vndr
./usr/share/X11/xkb/geometry/digital_vndr
./usr/share/X11/xkb/symbols/digital_vndr
./usr/lib/libgphoto2/2.4.6/digita.so
./usr/lib/python2.6/cgitb.pyc
./usr/lib/python2.6/cgitb.py
./home/kartik/Downloads/git-core_1.7.1-1.1_all.deb
./etc/ssl/certs/Digital_Signature_Trust_Co._Global_CA_3.pem
./etc/ssl/certs/Digital_Signature_Trust_Co._Global_CA_1.pem
./etc/ssl/certs/Digital_Signature_Trust_Co._Global_CA_2.pem
./etc/ssl/certs/Digital_Signature_Trust_Co._Global_CA_4.pem
./var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/KacstDigital.ttf
./var/lib/defoma/gs.d/dirs/fonts/KacstDigital.ttf
./lib/modules/2.6.31-14-generic/kernel/drivers/hid/hid-logitech.ko
./lib/modules/2.6.31-14-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-digitv.ko

---

### Post by dethmaShine on 2010-08-24
In Software sources:UbuntuSoftware:
All are checked except for source code

In Software sources:othersoftware:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

Thats all I can see!

---

### Post by dethmaShine on 2010-08-24
What repository should I install to get git?

---

### Post by dethmaShine on 2010-08-24
As I am working on a proxy, it looks like I cannot connect to the internet. When I type:

root@kt-linux:~/Downloads# nslookup security.ubuntu.com
Server:      <my server>
Address:    <my address>

** server can't find security.ubuntu.com: NXDOMAIN

---

