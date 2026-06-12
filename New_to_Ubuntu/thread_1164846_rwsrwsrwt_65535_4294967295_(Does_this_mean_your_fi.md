---
title: "?rwsrwsrwt 65535 4294967295 (Does this mean your file is corrupted?)"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by rybaxs on 2009-05-20
?rwsrwsrwt 65535 4294967295 (Does this mean your file is corrupted?)

---

### Post by Lampi on 2009-05-20
well - it IS a big file :D - permissions look allright - don't know about the question mark though. If you want to check the file system unmount this partition and run fsck -vfC /dev/<partition>

---

### Post by rybaxs on 2009-05-20
```

fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? 

```



WhAT SHOULD I DO? YES or NO?

---

### Post by Game Over on 2009-05-20
Maybe pose this question in a different section of the forum?
Beginner Talk might not be the place??
But I dunno, I'm still new to Linux. It's your call, buddy.

---

### Post by rybaxs on 2009-05-20
thanks !.. i don't know what's the outcome of this..


```

/dev/sda1: recovering journal
Clearing orphaned inode 6759227 (uid=1000, gid=1000, mode=0100600, size=32800)
Clearing orphaned inode 778254 (uid=1000, gid=1000, mode=0140755, size=0)
Clearing orphaned inode 4475442 (uid=0, gid=0, mode=0100644, size=0)
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>?        

/dev/sda1: e2fsck canceled.

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: ***** REBOOT LINUX *****
root@user-desktop:/media/disk/home/user/.purple/logs# fsck -vfC
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? yes    

Inode 24577 was part of the orphaned inode list.  FIXED.
Inode 24577 has imagic flag set.  Clear<y>? yes

Inode 24578 is in use, but has dtime set.  Fix<y>? yes

Inode 24579 was part of the orphaned inode list.  FIXED.
Inode 24580 is in use, but has dtime set.  Fix<y>? yes

Inode 24580 has imagic flag set.  Clear<y>? yes

Inode 24581 is in use, but has dtime set.  Fix<y>? yes

Inode 24582 was part of the orphaned inode list.  FIXED.
Inode 24583 is in use, but has dtime set.  Fix<y>? yes

Inode 24584 was part of the orphaned inode list.  FIXED.
Inode 24584 has imagic flag set.  Clear<y>? yes

Inode 24585 is in use, but has dtime set.  Fix<y>? yes

Inode 24585 has imagic flag set.  Clear<y>? 

```

---

### Post by Lampi on 2009-05-20
I said unmount the partition first - you should never filecheck a mounted ext3 partition! If this is your root partition you need to boot another linux. Best choice is your ubuntu livecd. Then run fsck on the *NOT* mounted partition!

---

### Post by rybaxs on 2009-05-20
> **Lampi said:**
> I said unmount the partition first - you should never filecheck a mounted ext3 partition! If this is your root partition you need to boot another linux. Best choice is your ubuntu livecd. Then run fsck on the *NOT* mounted partition!

yes, I already unmount the other disk. The best choice is to late. :'(

yay.. i've just unmounted the other disk, I have two hard drive mounted. I unmount the affected one. tsk tsk.. is there any other way i can recover my primarydisk? all my system won't boot up.. :(

---

### Post by Lampi on 2009-05-20
you boot the ubuntu cd in live mode - this way you can fsck every partiton, since none of them is mounted by default. Before you run fsck make sure none of them is mounted by mistake - if it tells you it IS mounted, *don't* just run the file check. This is one many misunderstandings a windozer has when he tries linux: windows actually *can* check filesystems on a mounted partition, linux filesystems mostly can't (ext4 left asside)

---

### Post by rybaxs on 2009-05-20
I was thinking that the fsck will automatically check the unmounted(DiskB), that's why I unmounted the affected disk(DiskB), but what happened was he fsck the mounted(DiskA). tsk tsk.. ok Im done with this one. I reformat (diskA) and installed the OS again. 

I've run the liveCD. with unmounted affected disk(DiskB). There are files that cannot be modified, opened nor delete. a single text file had the capacity of 40GB how could this be? when I check other files, they are more than 100GB. is this file corrupted? when I fsck the unmounted disk(DiskB) it always ask me to clear or fix.. is there anyway that he will give me "fix to all" or "clear to all"? I think this is too far. should I continue pressing Y ? I think I've press a million times. hehehe

thanks a lot Lampi.

---

### Post by rybaxs on 2009-05-20
other threads about this issue

click here:
[http://ubuntuforums.org/showthread.php?t=1164810](http://ubuntuforums.org/showthread.php?t=1164810)

---

### Post by lavinog on 2009-05-20
you can check all partitions by using this command:
```
sudo touch /forcefsck
```
Then reboot
It will force a check on all partitions in fstab

---

