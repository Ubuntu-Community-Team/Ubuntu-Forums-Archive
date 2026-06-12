---
title: "Extra Storage Drive"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by DamnLag on 2009-05-23
I am fairly new to Ubuntu. I have a computer with 2 HDs in it. I have installed Ubuntu onto the main drive. I have a second drive that I formatted to ext3 to use for extra storage. 

Here is the problem. I can't seem to figure out how to mount it. I have searched these forums.. and all I've really found is a billion how-to-mount ntfs/fat32 posts. Out of curiosity I formatted the drive to both ntfs and fat32.. Both times I rebooted and low and behold there was a new entry under "Places" menu each time I formatted the drive to something 'windowy'. 

What am I missing? Granted I am a total newb when it comes to all of this, but it's driving me nuts that any linux partition I create just won't seem to mount. Leads me to believe I have completely missed something here.

---

### Post by kpkeerthi on 2009-05-23
Lets take one step at a time. Its pretty easy.

Reformat it back to ext3. And post the outputs of the following commands:

```
sudo fdisk -l
```
```
mount
```
```
sudo blkid
```

---

### Post by DamnLag on 2009-05-23
1:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcef2cef2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1e2d1e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    5  Extended
```

2:

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/damnlag/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=damnlag)
```

3.

```
/dev/sda1: UUID="c2d2ff25-49d9-486e-9d20-d5df3f27ef97" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="4fab8391-cf52-4720-b71c-beb51d544fbd" 
```

---

### Post by kpkeerthi on 2009-05-23
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    5  Extended


Is this your other drive? It doesn't appear to be formatted. Format it to ext3, using [gparted]("http://www.ehow.com/how_4963426_format-usb-flash-drive-ubuntu.html"). Post back the outputs of the all the commands.

---

### Post by DamnLag on 2009-05-23
Well I feel like a git.. I didn't have any of the space allocated. How many times I did it and never even noticed. 

Now I just need to find a way to get it to stop mounting as root so I can write to it. I will try to tackle that next.

Sorry to waste your time for something so silly.

---

### Post by kpkeerthi on 2009-05-23
Assuming it is ext3,
1. Mount the partition using FSTAB
2. Change ownership of the mount point (assuming it is mounted to /media/Data):
sudo chown -R <user-name> /media/Data
3. Change permission:
sudo chmod -R 755 /media/Data
* Set this permission to your need.

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

