---
title: "How to: Mount Second Hard Drive"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by zutronius on 2009-02-03
I am trying to mount a second hard drive (/dev/sda) in my pc. 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007689

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30400   244187968+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000db3bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29646   238131463+  83  Linux
/dev/sdb2           29647       30401     6064537+   5  Extended
/dev/sdb5           29647       30401     6064506   82  Linux swap / Solaris
zach@zach-desktop:~$ sudo blkid
/dev/sdb1: UUID="90171dfc-e87a-481c-b888-779dbf0a0683" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="be83b286-b79f-48b5-bba0-e970ecc48295" 
/dev/sda1: UUID="8aad621d-6f4d-4fad-b1c3-630379f7f0e0" SEC_TYPE="ext2" TYPE="ext3" 

I have never mounted a hard drive in Ubuntu before and was wondering if someone could tell me how I go about doing this.

---

### Post by DavidBeijer on 2009-02-03
Well, to do this, you need two things: you need a the mounting point for your second harddisk. As you can derive from the data you posted in your question, that mounting point is /dev/sda1. 

The second thing you need is a point to mount your harddisk to. That will be the place where the disk is entered in your filesystem. You can basically choose that place, but there has to be a folder there. For CD and DVD drives, just as USB disks it is common to create such a folder in /media, for harddrives it is common to mount them in /mnt.

I will describe the procedure for a harddrive, since that is your question, but the same process applies for USB drives etc.

First of all you create the directory to mount the disk to. In your terminal you navigate to the mnt directory.

```
cd /mnt
```

Then you create the directory, let's say you want to call that 'data'

```
mkdir data 
```

Now you are ready to mount the drive. You do that using the 'mount' command. This command requires root privileges, so don't forget sudo.

```
mount /dev/sda1 /mnt/data 
```

That is basically all that there is to it!

---

### Post by taurus on 2009-02-03
Edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```

UUID=8aad621d-6f4d-4fad-b1c3-630379f7f0e0   /media/sda1   ext3   defaults   0   2
```
Save it and close down gedit window.  Now, create a new mount point and mount it.

```
sudo mkdir /media/sda1
sudo mount -a
df -h
```
If you want to write to /media/sda1 without using sudo or gksudo, you can change the ownership of /media/sda1 from root to your login name, _assuming_ your login name is zutronius.

```
sudo chown -R zutronius:zutronius /media/sda1
ls -la /media
```

---

