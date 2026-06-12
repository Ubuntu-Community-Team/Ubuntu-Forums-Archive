---
title: "Backing up old OSX files"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by cacapan on 2009-04-20
I want to completely get rid of OSX Leopard on my macbook, install Ubuntu Intrepid and use it exclusively. Whats the best way to transfer all my movies, photos, music, and files to my new Ubuntu system? How should I backup my files? Is there any issues that may arise from transferring hfs+ to ext3?
I have at my disposal a 30gb external hdd (formatted FAT32) and a working CD/DVD burner. The files I want to keep amount to about 50gb.
Before I fully erase OSX I want to make sure I can do this properly.
Any help would be greatly appreciated.

---

### Post by billgoldberg on 2009-04-20
Do you have any free space on your harddrive?

If so, make some space for an extra partition (50gb or more), format it as ext3 (or anything you like).

When you are ready, copy the files from your mac to the new partition on your harddrive.

You will need to use a live cd (Ubuntu for example) that has gparted on it to do the partitioning.

You can't do it from withing OSX.

Now I don't know if OSX supports ext3 (doubt it), so you can use to Ubuntu live cd to copy the files from your OSX partition to the newly created one.

Then you can install Ubuntu (tip: wait a week until the new Ubuntu version comes out) over the OSX partition.

I never actually don't this on a mac, only on normal pc's, but it should all be the same, unless some strange restrictions apply.

---

### Post by steve101101 on 2009-04-20
> **billgoldberg said:**
> Do you have any free space on your harddrive?

If so, make some space for an extra partition (50gb or more), format it as ext3 (or anything you like).

When you are ready, copy the files from your mac to the new partition on your harddrive.

You will need to use a live cd (Ubuntu for example) that has gparted on it to do the partitioning.

You can't do it from withing OSX.

Now I don't know if OSX supports ext3 (doubt it), so you can use to Ubuntu live cd to copy the files from your OSX partition to the newly created one.

Then you can install Ubuntu (tip: wait a week until the new Ubuntu version comes out) over the OSX partition.

I never actually don't this on a mac, only on normal pc's, but it should all be the same, unless some strange restrictions apply.

i believe this should work.

---

### Post by cacapan on 2009-04-20
Thanks for the quick replies. And thanks for the great idea goldberg.
I don't have 50gbs free but I might be able to make room for a partition after a little clean up.
I know Jaunty is coming out soon (I have beta on my eeepc;)) I have an Intrepid Live CD handy right now so its just convenient. I could always upgrade later. 
Thanks again. I'll give it a shot.

---

### Post by steve101101 on 2009-04-20
just be careful to make sure you don't lose your files.

---

