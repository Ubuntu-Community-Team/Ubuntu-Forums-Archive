---
title: "help with remote desktop"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by theozzlives on 2009-01-25
I can connect my laptop to my web server fine, but the web server box cannot connect to my laptop. The laptop is running 8.10 32 bit Desktop, The server is running 9.04 Alpha 3 32 bit Desktop. Any ideas?

---

### Post by llamakc on 2009-01-25
Have you installed any VNC software on the laptop yet? Gnome has a package called grdesktop that's a frontend for rdesktop (for the server).

```

apt-cache show grdesktop
Package: grdesktop
Priority: optional
Section: universe/x11
Installed-Size: 440
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Bart Martens <bartm@debian.org>
Architecture: i386
Version: 0.23+d040330-1
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.6.1-1), libcairo2 (>= 1.4.0), libgconf2-4 (>= 2.13.5), libglib2.0-0 (>= 2.14.0), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.8), libpango1.0-0 (>= 1.19.0), libpopt0 (>= 1.10), libsm6, scrollkeeper, rdesktop (>= 1.3.0-1), gconf2 (>= 2.10.1-2)
Filename: pool/universe/g/grdesktop/grdesktop_0.23+d040330-1_i386.deb
Size: 114032
MD5sum: 91b4418706e8e01b7d44664801a504fe
SHA1: 54e07d67c8cf29e5857d08cb8743671c0e701442
SHA256: f3c7b484697d84418ae09ef2d75e5389a2cb7f47cba4d2f09a42a8236715a737
Description: GNOME frontend for the rdesktop client
 grdesktop is a GNOME frontend for the remote desktop client (rdesktop).
 .
 It can save several connections (including their options), and
 browse the network for available terminal servers.
 .
  Homepage: http://www.nongnu.org/grdesktop/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

You will need something running ON the laptop to connect to it from the server box.

Vino is a nice server package.

```

 apt-cache show vino
Package: vino
Priority: optional
Section: gnome
Installed-Size: 2680
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Jordi Mallach <jordi@debian.org>
Architecture: i386
Version: 2.24.1-0ubuntu1
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libavahi-glib1 (>= 0.6.16), libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.71), libgconf2-4 (>= 2.13.5), libgcrypt11 (>= 1.4.0), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.17.0), libgnome2-0 (>= 2.17.3), libgnomeui-0 (>= 2.22.0), libgnutls26 (>= 2.4.0-0), libgtk2.0-0 (>= 2.14.1), libnotify1 (>= 0.4.4), libnotify1-gtk2.10, libx11-6, libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxtst6, zlib1g (>= 1:1.1.4), gconf2 (>= 2.10.1-2)
Suggests: vinagre, gnome-user-guide | gnome2-user-guide (>= 2.8.1)
Filename: pool/main/v/vino/vino_2.24.1-0ubuntu1_i386.deb
Size: 204264
MD5sum: ab0d4616fd147db96bd0def0b961a894
SHA1: 613aa542d18c62acd10bf61e21bfefd0ad1b833b
SHA256: 23f117ad39b4061daeee9b778fd957b16266133fe7a9d8b486bf8d44b0ead1be
Description: VNC server for GNOME
 VNC is a protocol that allows remote display of a user's desktop. This
 package provides a VNC server that integrates with GNOME, allowing you
 to export your running desktop to another computer for remote use or
 diagnosis.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop, mobile-mobile

```

---

### Post by theozzlives on 2009-01-26
K, I installed grdesktop and vino was already installed, still no dice, what now??? I've been haveing problems accessing my samba shares on my laptop, but my laptop can access the network fine if that helps. My laptop is wireless if that matters any.

---

### Post by theozzlives on 2009-01-26
```
Package: vino
Priority: optional
Section: gnome
Installed-Size: 2680
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Jordi Mallach <jordi@debian.org>
Architecture: i386
Version: 2.24.1-0ubuntu1
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libavahi-glib1 (>= 0.6.16), libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.71), libgconf2-4 (>= 2.13.5), libgcrypt11 (>= 1.4.0), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.17.0), libgnome2-0 (>= 2.17.3), libgnomeui-0 (>= 2.22.0), libgnutls26 (>= 2.4.0-0), libgtk2.0-0 (>= 2.14.1), libnotify1 (>= 0.4.4), libnotify1-gtk2.10, libx11-6, libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxtst6, zlib1g (>= 1:1.1.4), gconf2 (>= 2.10.1-2)
Suggests: vinagre, gnome-user-guide | gnome2-user-guide (>= 2.8.1)
Filename: pool/main/v/vino/vino_2.24.1-0ubuntu1_i386.deb
Size: 204264
MD5sum: ab0d4616fd147db96bd0def0b961a894
SHA1: 613aa542d18c62acd10bf61e21bfefd0ad1b833b
SHA256: 23f117ad39b4061daeee9b778fd957b16266133fe7a9d8b486bf8d44b0ead1be
Description: VNC server for GNOME
 VNC is a protocol that allows remote display of a user's desktop. This
 package provides a VNC server that integrates with GNOME, allowing you
 to export your running desktop to another computer for remote use or
 diagnosis.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop, mobile-mobile

ozzie@ozzie-laptop:~$ sudo apt-cache show grdesktop
Package: grdesktop
Priority: optional
Section: universe/x11
Installed-Size: 440
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Bart Martens <bartm@debian.org>
Architecture: i386
Version: 0.23+d040330-1
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.6.1-1), libcairo2 (>= 1.4.0), libgconf2-4 (>= 2.13.5), libglib2.0-0 (>= 2.14.0), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.8), libpango1.0-0 (>= 1.19.0), libpopt0 (>= 1.10), libsm6, scrollkeeper, rdesktop (>= 1.3.0-1), gconf2 (>= 2.10.1-2)
Filename: pool/universe/g/grdesktop/grdesktop_0.23+d040330-1_i386.deb
Size: 114032
MD5sum: 91b4418706e8e01b7d44664801a504fe
SHA1: 54e07d67c8cf29e5857d08cb8743671c0e701442
SHA256: f3c7b484697d84418ae09ef2d75e5389a2cb7f47cba4d2f09a42a8236715a737
Description: GNOME frontend for the rdesktop client
 grdesktop is a GNOME frontend for the remote desktop client (rdesktop).
 .
 It can save several connections (including their options), and
 browse the network for available terminal servers.
 .
  Homepage: http://www.nongnu.org/grdesktop/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

