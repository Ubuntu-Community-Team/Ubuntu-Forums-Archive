---
title: "Ubuntu Server: Hot Repartition?"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by xtomtomx on 2011-02-10
Hello Team,
I'm running Ubuntu server and would like to know if I can repartition without reinstall.

My server has 4 200 GB raid drives which are being used by the main Ubuntu 64 bit O/S and file system, but I have also 2 75 GB drives I want to add.(which are already installed.
Ubuntu recognizes these drives, but I want to add a total of 275 GB to ther Ubuntu O/S file system, essentially making use of all the disk space.

Is there a way to do this on the fly?


Thank you,

---

### Post by cariboo on 2011-02-10
Gparted or fdisk won't let you partition a disk if it is mounted, so unmount the drives and then you should be able to repartition the disks. Once done just remount the drives.

---

