---
title: "Cant complete Ubuntu update"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Scozer on 2010-10-03
Hi,

We're running 10.04LTS and each time we run Update Manager (or I try apt-get update in a terminal) the following error appears:

Failed to fetch cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Should we be worried about this error - it looks like it's referring to the old OS? I'd like my OCD sated and for there to be no errors, but I don't know if this is just an old 'dependency' or something like that....

Thanks for any insight!

Todd

---

### Post by yabbadabbadont on 2010-10-03
If you are using Gnome, then go to System->Administration->Software Sources.  Look through the various settings on each of the tabs to make sure that they only refer to Lucid.

---

