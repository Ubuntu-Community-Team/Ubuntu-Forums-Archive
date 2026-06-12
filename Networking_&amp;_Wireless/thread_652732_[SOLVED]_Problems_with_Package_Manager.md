---
title: "[SOLVED] Problems with Package Manager"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by Coppper on 2007-12-29
Hi everybody !!! 

I have a fresh Gutsy , and i have problems with the package manager ..  it doesn´t work . i always get a time-out message 

Please help , it's my first Linux experience

---

### Post by PmDematagoda on 2007-12-29
Execute:-
```
sudo apt-get update
```
in a terminal and post the complete output.

---

### Post by Coppper on 2007-12-29
0% [Conectando a archive.canonical.com (1.0.0.0)] [Conectando a archive.ubuntu.com (1.0.0.0)] [Conectando a security.ubuntu.com (1.0.0.0)] [Conectando a ftp 

thanks !!

---

### Post by Coppper on 2008-01-01
Proble with DNS , everything is now OK since i changed to OpenDNS

---

### Post by hackensack on 2008-01-01
Since you are new as am I; get ready for lots of frustration and constant downloading updating ./configure, make and make install, web searching and spending hours to get things working. 
(E.G.)
checking for GLIB - version >= 2.5.7... 
*** 'pkg-config --modversion glib-2.0' returned 2.13.5, but GLIB (2.14.1)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

This kind of stuff happens at almost every install and I do not see many changes in the world of Linux. The Dependencies go on and on and on seemingly never ending. But the key is persistence and determination.

---

### Post by Coppper on 2008-01-02
You have the Gutsy Gibbon distro ??? 
I think the package manager works fine , it's quite  easy to install new things

---

