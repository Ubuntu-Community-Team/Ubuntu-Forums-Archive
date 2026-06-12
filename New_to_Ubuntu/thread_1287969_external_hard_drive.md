---
title: "external hard drive"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by zapree on 2009-10-10
I'm trying to find and mount my hard drive, but when i plug it in nothing comes up.... Where do i find it or what command do i need to find it?
it's a seagate 250gb "external portable drive" So maby it's not compatible? 
Thanks
Patrick
ps. i did look under /media and i rebooted comp to see if that would do it.

---

### Post by skatinjj on 2009-10-10
run

```
sudo fdisk -l
```

That will give you your partition table and you can see which device is your external HDD

---

### Post by zapree on 2009-10-10
I ran fdisk -l and its not coming up with anything (it just skips to another prompt line, nothing in-between)

---

### Post by callan79 on 2009-10-10
> **zapree said:**
> I ran fdisk -l and its not coming up with anything (it just skips to another prompt line, nothing in-between)

Howdy,

Try that with sudo in front ...

```
sudo fdisk -l
```

Then, copy and paste that back here with in between CODE and /CODE tags.

Also, paste results of :

```
mount
```

Cheers
Callan

---

### Post by zapree on 2009-10-10
This is what i got from 

Code:

sudo fdisk -l


Code
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef90ef90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       24792    64934730    5  Extended
/dev/sda5           16709       24457    62243811   83  Linux
/dev/sda6           24458       24792     2690856   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16381637

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19080   153260068+  83  Linux
/dev/sdb2           19081       19457     3028252+   5  Extended
/dev/sdb5           19081       19457     3028221   82  Linux swap / Solaris
/Code

This is what i got from 

Code:

mount


Code:
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/patrick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=patrick)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/Code

---

### Post by callan79 on 2009-10-12
> **zapree said:**
> 
Disk /dev/sda: 203.9 GB, 203928109056 bytes
Disk /dev/sdb: 160.0 GB, 160041885696 bytes



Hi zapree,

From the above it would seem your system has only two disks ... one 200GB and one 160GB.

Is this right? You have two disks inside your machine?

If so, your Seagate 250GB isn't being seen by the system. Can you try :

```

lsusb

```

Also, perhaps try watching the syslog while you plug it in, see if anything exciting shows up!

```

tail -f /var/log/syslog

```

Cheers
Callan

---

### Post by Bartender on 2009-10-12
> **zapree said:**
> 
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


I interpreted the info a little differently.  The above looks like a usb connected drive to me, but only 160GB, not 250?  I'm probly wrong as usual..:confused:

---

