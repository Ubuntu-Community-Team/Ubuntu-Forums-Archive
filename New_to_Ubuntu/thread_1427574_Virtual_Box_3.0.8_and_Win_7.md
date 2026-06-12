---
title: "Virtual Box 3.0.8 and Win 7"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by ubu newb on 2010-03-11
Ubuntu 9.10 installed with wubi installer using win 7 pro 64 bit.  Installed Virtual Box 3.0.8.

How can I view and use my existing windows 7 and all that is installed?   I don't see any options to be able to.  When I view the file systems I see the 750 GB HD but it points to the 13.1 GB factory image.  I don't see the main HD at all.

---

### Post by Shii on 2010-03-11
VirtualBox only runs *images* of systems. It can't read your disk partition directly. However, you can convert your Windows partition to an image that VirtualBox can use:

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

Pay attention to the errors listed at the top before you run the commands at the bottom :)

---

