---
title: "Partition Problem, plas help!"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by TangChao on 2008-12-26
Today I reinstalled Ubuntu, my previous partition setting is:
/boot
/home (10G)
/
swap
I didn't delete /home partition for my new Ubuntu system because there is some important files in it, and I thought the system would automatically set it as my /home partition, however, when the new installation completed, I saw a separated 10GB Media, and I will enter my password to open it. I want to know how to make my new system recognize that previous /home partion as a folder in "Filesystem".
Many many thanks!!!

---

### Post by SlidingHorn on 2008-12-26
When you're setting up your partitions, you have to set the /home partition's mount point to  /home

---

### Post by taurus on 2008-12-26
I guess you forgot to tell the installer to mount that partition to /home (except not format it).  However, you can edit /etc/fstab and mount it to /home again if you wish.  

Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by TangChao on 2008-12-26
> **taurus said:**
> I guess you forgot to tell the installer to mount that partition to /home (except not format it).  However, you can edit /etc/fstab and mount it to /home again if you wish.  

Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

I thought If I tell the installer to mount that partition to /home, it would be formatted.
I typed sudo fdisk -l:
```

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad72ad72

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        2576      208845   83  Linux
/dev/hda3            2577        7285    37825042+   f  W95 Ext'd (LBA)
/dev/hda5            2577        4488    15358108+   7  HPFS/NTFS
/dev/hda6            4489        5704     9767488+  83  Linux
/dev/hda7            7164        7285      979933+  82  Linux swap / Solaris
/dev/hda8            5705        7163    11719386   83  Linux

Partition table entries are not in disk order

```
sudo blkid:
```

/dev/hda1: UUID="78A0C40FA0C3D1B4" LABEL="System" TYPE="ntfs" 
/dev/hda2: UUID="c04a4fe0-e990-478e-8763-64f56b08c237" TYPE="ext3" 
/dev/hda5: UUID="9A9006FB9006DE1F" LABEL="Media" TYPE="ntfs" 
/dev/hda6: UUID="83025ff0-2025-49ed-b566-0aaee3268eee" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda7: TYPE="swap" UUID="af90339d-fe6f-4455-8e6c-fd4e7f142d08" 
/dev/hda8: UUID="39cf02fc-656e-4d9b-a41d-78a208c09092" TYPE="ext3" 

```
cat /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=39cf02fc-656e-4d9b-a41d-78a208c09092 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda2
UUID=c04a4fe0-e990-478e-8763-64f56b08c237 /boot           ext3    relatime        0       2
# /dev/hda7
UUID=af90339d-fe6f-4455-8e6c-fd4e7f142d08 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
df -h:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda8              12G  2.1G  8.5G  20% /
varrun                189M  120K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
udev                  189M   68K  189M   1% /dev
devshm                189M   12K  189M   1% /dev/shm
lrm                   189M   38M  151M  20% /lib/modules/2.6.24-16-generic/volatile
/dev/hda2             198M   24M  164M  13% /boot
gvfs-fuse-daemon       12G  2.1G  8.5G  20% /home/tony/.gvfs
/dev/hda6             9.3G  8.1G  760M  92% /media/disk

```
What should I do then?

---

### Post by taurus on 2008-12-26
Actually, it won't format unless you put a check mark (in the box) next to the mount point.

However, now that it's over.  Let's edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
UUID=83025ff0-2025-49ed-b566-0aaee3268eee   /home   ext3   defaults   0   2
```
Save it.  

Then reboot.

---

### Post by TangChao on 2008-12-26
> **taurus said:**
> Actually, it won't format unless you put a check mark (in the box) next to the mount point.

However, now that it's over.  Let's edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
UUID=83025ff0-2025-49ed-b566-0aaee3268eee   /home   ext3   defaults   0   2
```
Save it.  

Then reboot.
Thank you, it works, but I got new error messages when login (I'm now in WinXP), the general meaning is the system can't find my account in the /home partition, and notice me that my session would end in less than 10 seconds, but I forgot create my root account, so I can't login in now. What should I do now?

---

### Post by taurus on 2008-12-26
Boot into recovery mode from GRUB menu and post the output of these commands here.

```
cat /etc/fstab
df -h
ls -la /home
tail -5 /etc/passwd
```
By the way, do you know that you can access your Ubuntu partitions from windows with fs-driver, [http://www.fs-driver.org/?](http://www.fs-driver.org/?)

---

### Post by TangChao on 2008-12-26
> **taurus said:**
> Boot into recovery mode from GRUB menu and post the output of these commands here.

```
cat /etc/fstab
df -h
ls -la /home
tail -5 /etc/passwd
```
By the way, do you know that you can access your Ubuntu partitions from windows with fs-driver, [http://www.fs-driver.org/?](http://www.fs-driver.org/?)

Yes, I used Ext2FS(?) before, will it work?

---

### Post by TangChao on 2008-12-26
> **taurus said:**
> Boot into recovery mode from GRUB menu and post the output of these commands here.

```
cat /etc/fstab
df -h
ls -la /home
tail -5 /etc/passwd
```
By the way, do you know that you can access your Ubuntu partitions from windows with fs-driver, [http://www.fs-driver.org/?](http://www.fs-driver.org/?)
I installed Ext2IFS, I tried to copy my current account into /home partition, but "access is denied", and I ran the code in recovery mode, still didn't work, I don't understand them. And "-5" means the folder ID in /home partition?

---

### Post by taurus on 2008-12-26
The last command, tail -5 /etc/passwd, means list the last 5 lines in /etc/passwd.  

You mean there were no outputs when you ran those commands from a recovery mode or you got an error message when you ran them?

---

### Post by TangChao on 2008-12-27
> **taurus said:**
> The last command, tail -5 /etc/passwd, means list the last 5 lines in /etc/passwd.  

You mean there were no outputs when you ran those commands from a recovery mode or you got an error message when you ran them?

Thanks for your help, I ran "adduser/passwd" in the recovery mode and created a new user, now I can login as root.:)

---

