---
title: "GRUB question"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Diametric on 2010-01-17
I've got an 80GB HD that I loaded Ubuntu on today.  It had Vista on it and during installation, I used the "new' grub utility to partition the drive (grub2, I think...still in beta).  My question is, I now want to delete the ntfs partition and allocate the whole HD to Linux, whats the easiest way to get his done?  Also, sometime in the not so distant future, I would like to load 7 on the same HD.  Will this be difficult if I allocate the whole HD to Ubuntu now?

Thanks All,

-Diametric

---

### Post by warfacegod on 2010-01-18
Use Gparted for partition operations. If you plan on installing 7 later on then leave space for it unallocated. Resizing the partition your OS is on *can* be damaging.

---

### Post by Diametric on 2010-01-18
thanks for the reply.  I think I'll just run VMWare instead of saving space on the HD...would be cool to learn that app anyway.

Cheers!

---

### Post by warfacegod on 2010-01-18
If your going to resize your Linux partition then do it from a LiveCD install disc and use Gparted.

---

