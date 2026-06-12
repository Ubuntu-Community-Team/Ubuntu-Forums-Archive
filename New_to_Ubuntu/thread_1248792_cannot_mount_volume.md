---
title: "cannot mount volume"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by Sourien on 2009-08-24
true beginner here, so dumbed down language please.  I'm running ubuntu 8.04 and I had an external hard drive working last night.  I tried to right click the icon on my desktop and unmount it after I disconnected the drive and absolutely nothing happened.  Today, I tried to connect it again and I got an error message, saying  "cannot mount volume"  it also says that the logfile indicates an unclean shutdown and that it's unable to mount because ntfs is in use.  any help at all is appreciated.

---

### Post by mikewhatever on 2009-08-24
You have to unmount volumes before disconnecting, and not the other way around. Please post the output of **sudo fdisk -l** with the hdd in question connected.

---

### Post by TheLions on 2009-08-24
> **Sourien said:**
> true beginner here, so dumbed down language please.  I'm running ubuntu 8.04 and I had an external hard drive working last night.  I tried to right click the icon on my desktop and unmount it after I disconnected the drive and absolutely nothing happened.  Today, I tried to connect it again and I got an error message, saying  "cannot mount volume"  it also says that the logfile indicates an unclean shutdown and that it's unable to mount because ntfs is in use.  any help at all is appreciated.

boot into windows, connect the drive, disconnect it by "safety remove hardware", boot into ubuntu

or 
install "Partition Manager"
BE VERY CAREFULL
select your drive
unmount it if ain't already
Partition->Check

---

### Post by doas777 on 2009-08-24
> **Sourien said:**
> true beginner here, so dumbed down language please.  I'm running ubuntu 8.04 and I had an external hard drive working last night.  I tried to right click the icon on my desktop and unmount it after I disconnected the drive and absolutely nothing happened.  Today, I tried to connect it again and I got an error message, saying  "cannot mount volume"  it also says that the logfile indicates an unclean shutdown and that it's unable to mount because ntfs is in use.  any help at all is appreciated.

ok, always unmount BEFORE disconnecting. Windows is exactly the same in that regard.

the easiest way to fix it is to connect it to a windows pc, and reboot. the reboot will close your log so that shoudl be addressed. then run a chkdsk on it while you have it attached (since theres no good alternative to checkdsk that runs in linux for NTFS).

if not, you can force the mount or use 'ntfsfix' and cross your fingers. pulling a mounted drive is a very dangerous thing to do. it can cause hardware failures in addition to file system aberations.

---

### Post by mikewhatever on 2009-08-24
> **TheLions said:**
> boot into windows, connect the drive, disconnect it by "safety remove hardware", boot into ubuntu

or 
install "Partition Manager"
BE VERY CAREFULL
select your drive
unmount it if ain't already
Partition->Check

Assuming Windows is available to the OP, wouldn't it make more sense to check the 'dirty' partition in Windows?

---

### Post by Sourien on 2009-08-24
> **mikewhatever said:**
> You have to unmount volumes before disconnecting, and not the other way around. Please post the output of **sudo fdisk -l** with the hdd in question connected.



Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bef3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29645   238123431   83  Linux
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc2d79cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2       60801   488375968+   7  HPFS/NTFS


There's what I got

---

### Post by sandyd on 2009-08-24
> **Sourien said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bef3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29645   238123431   83  Linux
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc2d79cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2       60801   488375968+   7  HPFS/NTFS


There's what I got
```

sudo mkdir /media/sdb5
sudo mount -t ntfs-3g /dev/sdb5 /media/sdb5 -o force

```
please remember to unmount a volume before shutting down.
hard-shutting down your computer will also cause this.

if it still doesn't work,
```

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb5

```
should sort you out

and if the mkdir gives an error, don't worry about it.

---

### Post by mikewhatever on 2009-08-24
Hey carlee,
I was going to post similar instructions to yours with the difference of having to mount the ntfs partition. Why do you need to force mount it? Shouldn't it be unmounted during the check?

---

### Post by doas777 on 2009-08-24
the force is only needed if the log file is not yet closed. it is a little risky, so the ntfs-3g makes you use the option explicitly. once the drive is mounted, the op can unmount it to fix the log, and then mount normally.

---

### Post by freegeeky on 2009-08-26
I am new to Ubuntu and am having a similar cannot mount disk error.     

Here's the result of sudo fdisk -l: 
> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb684484c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9544    76662148+  83  Linux
/dev/sda2            9545        9729     1486012+   5  Extended
/dev/sda5            9545        9729     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         976     7839698    b  W95 FAT32


Is the solution going to be the same for a fat32 fs as it is for ntfs?

---

### Post by doas777 on 2009-08-26
> **freegeeky said:**
> I am new to Ubuntu and am having a similar cannot mount disk error.     

Here's the result of sudo fdisk -l: 


Is the solution going to be the same for a fat32 fs as it is for ntfs?

hmmm. FAT doesn't do journaling so there shouldn't be a log that fails to close.

what is the specific error that you are experiencing?

---

