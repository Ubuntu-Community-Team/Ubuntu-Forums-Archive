---
title: "Nautilus Icons  size doesn't change anymore."
date: 2011-05-20
forum: New to Ubuntu
---

### Post by parthgadhia on 2011-05-20
[http://www.flickr.com/photos/63193964@N08/5740675642/](http://www.flickr.com/photos/63193964@N08/5740675642/)

Hello,
I'd resized my nautilus icons to 50% zoom, which worked perfectly. 
But now, it's stuck there. Doesn't change anymore, even when I change the zoom levels back to 100% as shown in the image.

How can I change them back to their default size?

I googled it, and apparently it was a bug, but couldn't find out if it was fixed or not. 

```
ProblemType: Bug
Architecture: i386
Date: Fri Jan 15 18:47:48 2010
DistroRelease: Ubuntu 10.04
ExecutablePath: /usr/bin/nautilus
InstallationMedia: Ubuntu 10.04 "Lucid Lynx" - Alpha i386 (20100113)
Package: nautilus 1:2.29.1-0ubuntu2
ProcEnviron:
 LANG=en_GB.utf8
 SHELL=/bin/bash
ProcVersionSignature: Ubuntu 2.6.32-10.14-generic
SourcePackage: nautilus
Tags: lucid
Uname: Linux 2.6.32-10-generic i686
```

This is the bug apparently. :confused:

Thanks. :)

EDIT: Couldn't embed the image, so put the link.

---

### Post by ajgreeny on 2011-05-20
All I can suggest is renaming the ~/.gconf/apps/nautilus folder, then restarting X by logging out.

If that does not help it could be worth trying to purge nautilus, which will remove all the configurations in the filesystem, and then straight away re-installing it, but take a note of what else nautilus takes with it when you purge it, and make sure you re-install those packages as well.

---

### Post by jerrrys on 2011-05-20
i ran across this in ubuntu and had to right click and resize one window at a time, a real party killer.

---

### Post by parthgadhia on 2011-05-21
Argh..!!
hehe the first option i can't understand one bit, and the second option's too tedious!!

guess I'll just live with small icons.. :)

Thanks..

---

