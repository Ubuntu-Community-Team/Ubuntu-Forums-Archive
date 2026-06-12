---
title: "VNC in tty"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by elvinatom on 2007-06-16
I tried several vnc-viewers to access a vnc-server (linuxvnc) in tty, but all viewers seem to need x to display the remote console.  Is there any vnc-viewer out there that can run in pure tty (no x-server)?

---

### Post by popey on 2007-06-16
alan@mother:~$ apt-cache show directvnc
Package: directvnc
Priority: optional
Section: universe/misc
Installed-Size: 112
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian QA Group <packages@qa.debian.org>
Architecture: i386
Version: 0.7.5-8build1
Depends: libc6 (>= 2.5-0ubuntu1), libdirectfb-0.9-25, libjpeg62, zlib1g (>= 1:1.2.1)
Filename: pool/universe/d/directvnc/directvnc_0.7.5-8build1_i386.deb
Size: 27124
MD5sum: 3d948a40e2ed5ee029718b0ceffff443
SHA1: d7ce1259e64073d0d31f292617299b2a77ab8da3
SHA256: 9438cd231dbeee993b7eff2f81a630c998c18a4d2eae547a4f4bd85395a05b46
Description: VNC client using the framebuffer as display
 DirectVNC is a client implementing the remote framebuffer protocol (rfb)
 which is used by VNC servers. If a VNC server is running on a machine you
 can connect to it using this client and have the contents of its display
 shown on your screen. Keyboard and mouse events are sent to the server, so
 you can basically control a VNC server remotely.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by elvinatom on 2007-06-16
Thank you!
I'll give that a try ...

---

