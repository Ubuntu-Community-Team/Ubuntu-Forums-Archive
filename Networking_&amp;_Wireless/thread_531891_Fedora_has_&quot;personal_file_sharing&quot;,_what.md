---
title: "Fedora has &quot;personal file sharing&quot;, what is ubuntu's equvilant?"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by Fittersman on 2007-08-22
what is ubuntu's equivilant to fedoras personal file sharing? that is a really nice option to have, you can put all your files out for the network to see, but only if they know the correct password. How would you do that in ubuntu?

---

### Post by scxtt on 2007-08-22
it's part of gnome: gnome-file-share-properties

---

### Post by Fittersman on 2007-08-22
how do you do that?

---

### Post by scxtt on 2007-08-22
try typing **gnome-file-share-properties** into a terminal window (assuming you're using a recent version of gnome).

---

### Post by scxtt on 2007-08-23
found the package that provides it: **gnome-user-share**
```
scxtt@feisty [ /home/scxtt ]
:> aptitude search gnome-user-share
p   gnome-user-share                - User level public file sharing via Apache 
scxtt@feisty [ /home/scxtt ]
:> aptitude show gnome-user-share
Package: gnome-user-share
State: not installed
Version: 0.10-4
Priority: optional
Section: universe/gnome
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 520k
Depends: libavahi-client3 (>= 0.6.13), libavahi-common3 (>= 0.6.10),
         libavahi-glib1 (>= 0.6.12), libc6 (>= 2.5-0ubuntu1), libgconf2-4 (>=
         2.13.5), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.12.9),
         libgtk2.0-0 (>= 2.10.3), liborbit2 (>= 1:2.14.1), libselinux1 (>=
         1.32), libx11-6, gconf2 (>= 2.12.1-4ubuntu1), apache2 (>= 2.2), apache2
         (< 2.3), avahi-daemon
Description: User level public file sharing via Apache and WebDAV
 gnome-user-share is a small package that binds together Apache, avahi and GNOME
 to bring easy to use user-level file sharing to the masses.
```

---

### Post by Fittersman on 2007-08-24
thx alot :)

..but i already figured out how to do what i need: :P
[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

---

