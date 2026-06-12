---
title: "Two partitions to /home"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by 4moxy4 on 2009-02-20
I have two hard drives: /dev/sda houses a boot, swap, and / partition and /dev/sdb houses a swap and my /home. Sda has 162.7 gigs of unallocated space that I would like to use to store video, music, docs, pictures. Basically I would like partition the unallocated space to be an extension of my /home. Is this possible or something else like that? Here is my disk info...



Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  83  Linux
/dev/sda2              25         510     3903795   82  Linux swap / Solaris
/dev/sda3             511        3082    20659590   83  Linux

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30029   241207911   83  Linux
/dev/sdb2           30030       30394     2931862+  82  Linux swap / Solaris

---

### Post by PointyWombat on 2009-02-20
You could create a filesystem on that empty partition and persistent mount that directory to a mount point in your homedir through fstab.

---

### Post by Bachstelze on 2009-02-20
> **PointyWombat said:**
> You could create a filesystem on that empty partition and persistent mount that directory to a mount point in your homedir through fstab.

Another approach would be to set up LVM and/or RAID to have it all mounted on /home and have all the space available at will. Of course, it will be a bit more complicated to set up (and will require backup of all the original data first), but it might be worth it in the end.

---

### Post by northern lights on 2009-02-20
I'd suggest you mount it to the standard /media and create a symlink to /media/YourMountpoint in /home/YourUsername/

Create a new partition (gParted) sda4, I'll call it "Storage" for now, alter to your liking. I'd further suggest using xfs as the filesystem, rather than ext3, if you want it to house large files (video). Subsequently edit fstab```
gksu gedit /etc/fstab
```and append it by something along the lines of```
/dev/sda4	/media/storage  xfs	users,rw,noatime	0       0
```Last, create a symlink in /home```
ln -s /media/storage /home/YourUsername/storage

```

---

### Post by jerome1232 on 2009-02-20
> **HymnToLife said:**
> Another approach would be to set up LVM and/or RAID to have it all mounted on /home and have al the space available at will. Of course, it will be a bit more complicated to set up (and will require backup of all the original data first), but it might be worth it in the end.

+1 for lvm, although it is a bit more complicated initially, I find LVM a joy to work with once I learned it. LVM is very flexible. You can grow file systems while they are mounted without regard to where they are physically located, you can move them to other physical volumes while they are mounted, you can create snapshots for consistent backups without bringing a service down, you can mirror/strip volumes for reliability/speed.

Just today I migrated My entire system (which uses LVM) from one disk  to another without having to bring my computer system down or unmount any partitions.

---

### Post by 4moxy4 on 2009-03-10
> **northern lights said:**
> Create a new partition (gParted) sda4, I'll call it "Storage" for now, alter to your liking. I'd further suggest using xfs as the filesystem, rather than ext3, if you want it to house large files (video).


Thank you for the replies. GParted does not give me the option of creating a partition with xfs, as it is greyed out. Can I work around this, or will I just have to go with another file system?

---

### Post by jerome1232 on 2009-03-10
You probably just need to install the xfs utilites

```
sudo apt-get install xfsprogs
```

---

