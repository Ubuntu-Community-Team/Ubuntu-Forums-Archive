---
title: "Automatically Rebuild Grub... live cd?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by earthpigg on 2008-12-15
is there any live cd/distro out there that, when inserted, will do something like this:

1. ask what partition you want your grub to reside on.
2. automatically detect all kernels on any/all specified partitions.
3. let you name them if you want... or just call them "partition 1, kernel <filename>" or something similar.
4. build a grub menu.

does this exist?

(reason: so i can distro hop without being smart enough to manually play with config files and modify my MBR and all that stuff. :) )

---

### Post by Sorivenul on 2008-12-15
You may be interested in [SuperGrubDisk]("http://www.supergrubdisk.org/") - it can do a lot.

---

### Post by bumanie on 2008-12-16
Alternate installation cd's gives one more control, over where grub gets installed than do live cd's. There is a bootloader named GAG that is OS independent, sits on the first (normally empty) track of your hard drive and is able to control up to 9 OSes. It is independent of the mbr and you can add/remove OSes without needing to re-configure any lists. That may be worth looking at, as long as you don't want more than 9 OSes at the one time.

---

