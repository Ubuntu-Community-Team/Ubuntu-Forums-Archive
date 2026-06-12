---
title: "Cant format Thumb Drive"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by iohern on 2011-07-10
I Have a centon datastick and i need to format it but every time i try to do any thing from within disk utility i get a error box saying "One or more partitions are busy on /dev/sdc". Is the any way to fix this

---

### Post by spiky001 on 2011-07-10
The disc has to be unmounted 1st

---

### Post by seawolf167 on 2011-07-12
Aye, unmount the drive then you can use gparted to format it. If you want this drive usuable on Windows-based computers you'll want to format it in NTFS, which requires that you get an additional package for NTFS support

```
sudo apt-get install ntfsprogs
```

EDIT: Use Fat32 not NTFS for flash drives unless you need file support for >4GB files, I was thinking about an external hard drive when I wrote the post - thanks to Rex for catching this!

---

### Post by Rex Bouwense on 2011-07-12
Oops.  I have been formatting flash drives with FAT32.  I thought I could use them in Microsoft Windows environments.  Is that wrong.

---

### Post by seawolf167 on 2011-07-12
> **Rex Bouwense said:**
> Oops.  I have been formatting flash drives with FAT32.  I thought I could use them in Microsoft Windows environments.  Is that wrong.

Sorry, I was wrong in my previous post - I was thinking an external hard drive. Fat32 is the way to go for flash drives since it doesn't have a journaling system. Thanks for the catch!

---

