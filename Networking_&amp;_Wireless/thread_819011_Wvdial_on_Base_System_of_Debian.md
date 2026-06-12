---
title: "Wvdial on Base System of Debian"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by DeVonne on 2008-06-04
Hello, I just installed the base system for Debian.

I need to know how to install wvdial on it I do not have an Ethernet connection, it is a usb modem and I use wvdial on Ubuntu.

Is there a way to install wvdial onto the Debian system with the Ubuntu cd with apt-get? so it can get all the dependencies?

Debian base system is just command line and has like almost no packages, but I need internet so thanks for the help in advance

---

### Post by jpkotta on 2008-06-08
You can probably use ```
sudo apt-cdrom add
```
It might not work out too well.  If it tries to install a new libc or kernel or other major stuff, you're better off installing the packages by hand```
sudo dpkg -i /path/to/package.deb
```
If you have access to a fast connection, you could get just about all the debian packages on CDs.

---

