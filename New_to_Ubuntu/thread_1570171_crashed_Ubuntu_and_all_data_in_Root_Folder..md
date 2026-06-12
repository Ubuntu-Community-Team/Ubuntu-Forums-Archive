---
title: "crashed Ubuntu and all data in Root Folder."
date: 2010-09-07
forum: New to Ubuntu
---

### Post by smolik2005 on 2010-09-07
I was running ubuntu 9 for about half year before its crashed because I have installed xp afterwards. I had photographs and videos of 30 GB which most likely to be in the root folder.

I ran Ubuntu 10 from USB today and fortunate could see the old partition of the hard disk but can't open the root folder.. I have looked everywhere on the hard and nowhere these photos. But it must be there because the hard disk is quite full.

I know the old login name and the password when I used ubuntu 9.



Many Cheers!:popcorn:

---

### Post by garyedwardjohnston on 2010-09-07
using the live system, just mount the partition and search

---

### Post by jtarin on 2010-09-07
[How to use the Live CD to mount another Ubuntu installation]("https://help.ubuntu.com/community/LiveCdRecovery")

---

### Post by mapes12 on 2010-09-08
Boot your machine with the Live CD.

Launch Nautilus with super user permissions like this in Terminal ```
gksudo nautilus
```Navigate to the stuff you want to copy then copy it to external media.

Reinstall a fresh version of Ubu but this time put /home on its own partition. Copy back your stuff.

That's it! 

):P

---

