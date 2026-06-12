---
title: "uninstall"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2009-12-12
presently i'm using ubuntu 9.04

my question is how to uninstall ubuntu ?

---

### Post by 3rdalbum on 2009-12-12
If you used Wubi to install Ubuntu, then use the Add/Remove Programs function in Windows to remove Ubuntu.

If you installed Ubuntu by booting up the live CD and running the installer proram:

Erase the partition it resides on. If you dual-boot with Windows, you'll need to boot up the Windows CD and run the "fixmbr" program from the Windows command-line in order to be able to boot up Windows again.

---

### Post by cartisdm on 2009-12-12
If you already have another OS installed (meaning you have a dual-boot setup) you can just erase the partition using a liveCD of GParted then format that space in a usable format for your other OS (NTFS, ext4, etc)

Or simply just install something else overtop

---

### Post by ~sHyLoCk~ on 2009-12-12
Format partition and "FIXMBR"

---

### Post by 1991sudarshan on 2009-12-13
how to formate the partition?

---

### Post by ~sHyLoCk~ on 2009-12-13
> **1991sudarshan said:**
> how to formate the partition?

Install a partition manager in your windows , I'd recommend using Acronis Disk Director.

---

### Post by cartisdm on 2009-12-13
> **1991sudarshan said:**
> how to formate the partition?

Out of curiosity, how did you end up w/ Ubuntu on your HDD in the first place?

---

