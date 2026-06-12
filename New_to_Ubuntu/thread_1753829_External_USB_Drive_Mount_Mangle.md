---
title: "External USB Drive Mount Mangle"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by widda on 2011-05-09
Problem is with 120gb usb drive. Having big trouble getting head around umount, mount, mount point, fstab and mtab, /media/** , UUIDrw etc and how or even if they all relate to each other, or for that matter to my problem!  
Immediate problem is copying Music directory back to PC after trashing PC Music contents. Too slow, or rather, does 50Mb or so quick then hangs forever.
Tried command line cp, but : Drive had been named "New Volume" by system, (after reformatting it as cure for prior dead-end) and of course the space renders its name as simply "New", and sez 'no such dir'.
 OK
Next I try renaming, and here I start to get lost in all the mount stuff, BUT I DO notice that this external drive is called different things,  sdb1, sdc, and sdc1! (see screenshots).
I'm also prompted sometimes that it's not listed in fstab.
Greatly appreciate if anyone could point to an exit

---

### Post by widda on 2011-05-09
aha, now I HAVE renamed it by using "sdb1" in Community Documentaion advice for renaming drives - I had overlooked it amongst combinations of names/instructions.
So at least I can now try terminal for cp actions (I think)

---

