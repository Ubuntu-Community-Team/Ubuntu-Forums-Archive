---
title: "update from 9.10 to 10.04 and now 2 linux-swap"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by dreamquartz on 2010-05-02
I updated from 9.10 to 10.04, using the update function via **Update Manager**, but I am looking at** GParted** and see he following:

_Partition         File System  Mount Point   Size             Used          Unused        Flags_
/dev/sda1      ext4            /                      7.14 GB       6.28 GB   875.75 MB   boot
/dev/sda2      extended                         384.37 MB              ---               ---
   /dev/sda5   linux-swap                       384.34 MB              ---               ---
   
_Partition         File System   Label           Size             Used          Unused       Flags_
/dev/sdb1       ext3             HOME            14.23 GB   664.10 MB   13.58 GB    boot
/dev/sdb2       extended                          15.83 GB              ---             ---
   /dev/sdb5    ext4                                 15.12 GB       2.24 GB   12.89 GB
   /dev/sdb6    linux-swap                      721.64 MB              ---             ---

Do I have now 2 installs of 10.04 or are there left overs from 9.10?

Can anything be done about it?

Thx in advance
Dreamquartz

---

### Post by -humanaut- on 2010-05-02
Thats strange. try opening a terminal and type sudo fdisk -l and post back i'd be interested in see what that has to say. You are using multiple harddrives right?

---

### Post by dreamquartz on 2010-06-25
Reinstalled everything and was able to sort it out that way.

---

### Post by Jakiejake on 2010-06-25
> **dreamquartz said:**
> Reinstalled everything and was able to sort it out that way.

Awesome It should be alot faster now!
Enjoy! :p:lolflag::popcorn:

---

### Post by Stigmata13 on 2010-06-26
> **dreamquartz said:**
> Reinstalled everything and was able to sort it out that way.
Backing up and doing a fresh install is always a much better alternative to upgrading, its the recommended way of doing things, you can avoid many bugs that way :)

---

