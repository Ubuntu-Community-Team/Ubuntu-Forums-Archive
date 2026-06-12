---
title: "USB Thumbdrive?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Spiritous on 2009-04-25
I've just got 2 days ago, Ubuntu 9.04, and I plugged in my USB Thumbdrive, and when I try to open it in My Computer I get : ```
Unable to Mount location: No media in drive
```I know for a FACT there is music, video and pictures on there... Whats going on? I've got a[SIZE=1] SanDisk Micro Skin USB Flash Drive 4GB...
[/SIZE]

---

### Post by fahadsadah on 2009-04-25
Open a terminal, and type
```
sudo fdisk -l
```
please. You may be asked for a password.

---

### Post by Spiritous on 2009-04-25
Nope still same error when i try to open : /

---

### Post by fahadsadah on 2009-04-25
Sorry, I should have made it more clear.
Please can you paste the output of the above command here, so we can help you.

---

### Post by Spiritous on 2009-04-25
> **fahadsadah said:**
> Sorry, I should have made it more clear.
Please can you paste the output of the above command here, so we can help you.
Sorry :P 

```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18237   146488671    7  HPFS/NTFS
/dev/sda2           18238       30394    97651102+   5  Extended
/dev/sda5           18238       18486     2000061   82  Linux swap / Solaris
/dev/sda6           18487       30394    95650978+  83  Linux

```

---

### Post by fahadsadah on 2009-04-25
It doesn't seem to recognise that disc.
Please post the output of
```
ls /dev/sd*
```

---

### Post by Spiritous on 2009-04-25
```
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sda6  /dev/sdb

```

---

### Post by fahadsadah on 2009-04-25
That drive doesn't seem to be partitioned.

---

### Post by kpkeerthi on 2009-04-25
With your USB drive plugged in, post the output of
```
mount
```

---

### Post by Spiritous on 2009-04-25
> **kpkeerthi said:**
> With your USB drive plugged in, post the output of
```
mount
```

```
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/simon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=simon)
/dev/sda1 on /media/C: Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

---

### Post by fahadsadah on 2009-04-25
It's not mounted, because it's apparently not partitioned.
Was it partitioned on a Mac by any chance?

---

### Post by Spiritous on 2009-04-25
Nope, XP...

---

### Post by fahadsadah on 2009-04-25
Does XP show the data on the drive?

---

### Post by Spiritous on 2009-04-25
Yes

---

### Post by Spiritous on 2009-04-25
Shall I try going to XP and Formatting? Or I don't know :p I have nothing vital on there

---

### Post by fahadsadah on 2009-04-25
I would recommend formatting it FAT from Ubuntu.

---

### Post by Spiritous on 2009-04-25
> **fahadsadah said:**
> I would recommend formatting it FAT from Ubuntu.
Ok, I'll say if it works...

---

### Post by Spiritous on 2009-04-25
Yet ANOTHER problem! I'm formatting with Gnome Format and the error: ```
Error Opening /dev/sdb: Permission Denied
```AUI(*(*QR*(QHRHAPR!

Shall I format on XP?

---

### Post by fahadsadah on 2009-04-25
OK, do that.

---

### Post by Spiritous on 2009-04-25
Ok, i find the USB is corrupted because I pulled out last night HOW DO I FIX D:?! I can't Format or do anything :/?

---

### Post by Spiritous on 2009-04-25
Is there an app or something... because i've looked everywhere.

---

### Post by kpkeerthi on 2009-04-25
Boot with Ubuntu live cd
Insert your USB stick
Press ALT+F2 and enter **gparted**. I think its also available System -> Administration -> Disk Partition menu.
It should find your USB stick. If not, select it from the drop down at the top.
Right-click on the partition, choose Delete and click Apply. 
Then right-click, choose New and set is as FAT32. 
Click Apply. Done.

---

### Post by Spiritous on 2009-04-25
> **kpkeerthi said:**
> Boot with Ubuntu live cd
Insert your USB stick
Press ALT+F2 and enter **gparted**. I think its also available System -> Administration -> Disk Partition menu.
It should find your USB stick. If not, select it from the drop down at the top.
Right-click on the partition, choose Delete and click Apply. 
Then right-click, choose New and set is as FAT32. 
Click Apply. Done.

Trying now ;)

---

### Post by Spiritous on 2009-04-25
Nope, In the drop down menu there is only my HD, No Thumbdrive

Apparently there is a really good App in XP, i'll go try it out...

---

### Post by Spiritous on 2009-04-25
Strange, I can access files and stuff on XP now, Not ubuntu, same error O.o?

*Edit* Success, i managed to format with XP... :)

---

