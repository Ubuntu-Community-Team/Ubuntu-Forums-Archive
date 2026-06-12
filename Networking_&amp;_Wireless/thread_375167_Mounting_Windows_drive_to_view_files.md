---
title: "Mounting Windows drive to view files"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by geovino on 2007-03-03
I have just install 6.10 on a new pc and I want to see my windows drive to access files, here's my fdisk -l:
davek@davek-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS
davek@davek-desktop:~$ 

What do I do to access windows /dev/sdb1 without having to have a desktop icon, can I just go to network places or something like that to see the windows files? 

Thanks

---

### Post by ingo on 2007-03-04
put sda in your /etc/fstab file

search the forum or tags for fstab and you will find what you are looking for.

hth

---

### Post by geovino on 2007-03-05
Got it... Problem Solved:)

---

