---
title: "Installer not finding partitions"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by eifersucht9 on 2008-12-31
Hi all, I am very excited about Ubuntu and have been using the Live CD for about two weeks.  I am ready to install!  When I try to install from the Live cd it wont find any partitions.  I have a read all the other thread's about this but must be missing the fix. The disk has 3GB ntsb for windows.  Using acronics I created a 15GB EXT3 partition and a 1GB swap.  Still nothing.  Here is my sudo fdisk -l    Thanks all for the help!

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50e650e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         468     3759178+   7  HPFS/NTFS
/dev/sda2   *         469        2296    14683410   83  Linux
/dev/sda3            2297        2432     1092420   82  Linux swap / Solaris

---

### Post by taurus on 2008-12-31
Did you pick the Manual option when you get to the partition screen and tell the installer to mount /dev/sda2 as / and format it?

---

### Post by talsemgeest on 2008-12-31
So, just to clarify, when you get to the partitioning section of the installer, select manual and click next, the next page comes up blank?

---

### Post by eifersucht9 on 2008-12-31
Sorry, wasn't too clear on that.  When I get to the prep. partition screen it searches for partitions then doesn't show anything. I guess it it not picking up my HDD. Also, the options below where the partitions should be are grey and I can't click them.  Thus, no manual option is even displayed .  If i click next it wont continue because nothing has been selected. Thanks again

---

### Post by unutbu on 2008-12-31
The installer's partition editor will not list a drive if its partitions are mounted. So make sure all partitions are unmounted before you start the installer. 

You can check which partitions are mounted by typing
```

mount

```
and you can unmount a partition (say /dev/sda2) by typing
```

sudo umount /dev/sda2
```

---

### Post by eifersucht9 on 2008-12-31
Ok when I give the mount command this is what I get. 

ubuntu@ubuntu:~$ mount
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /cdrom type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/scd0 on /media/Ubuntu 8.10 i386 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=999,utf8)


Looking in GParted the only drive partition that I have the option to unmount is /dev/sda1.  When I do it says "could not unmount, /cdrom: device is busy.  If I reformat the NTFS partition I understand it will get rid of windows and that is ok, But will this get me anywhere?

---

### Post by unutbu on 2008-12-31
Hm. What happens if you try the following:

Reboot the LiveCD.

You will be asked if you wish to install Ubuntu or try it out without installing. Select the option to install Ubuntu.

Perhaps by going to the graphical desktop environment, Ubuntu is detecting your hard drive's partitions and mounting them automatically. I believe -- though I could be wrong -- that if you select the option to install Ubuntu directly without going to the graphical desktop, the hard drive partitions will remain unmounted.
How about you try it and see? Let us know how it goes.

---

