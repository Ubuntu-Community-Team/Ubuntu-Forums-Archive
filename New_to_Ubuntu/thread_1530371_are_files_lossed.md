---
title: "are files lossed"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-13
Hi,

I formated an external hdd and seemed to have successfully transfered many files to it. However it's icon doesnt show up on my desktop now. and Gparted claims the thing is "Unallocated". Is that certain there's nothing on there?

I hope this will tell you and me:

nnjond@nnjond-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nnjond/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nnjond)
nnjond@nnjond-desktop:~$ sudo fdisk -l
[sudo] password for nnjond: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea053

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60239   483864576   83  Linux
/dev/sda2           60239       60802     4519937    5  Extended
/dev/sda5           60239       60802     4519936   82  Linux swap / Solaris

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e67e

   Device Boot      Start         End      Blocks   Id  System
nnjond@nnjond-desktop:~$ 


Thanks.

---

### Post by HermanAB on 2010-07-13
Unplug the disk, wait a few seconds for the dust to settle, then plug it back in again.  That should remount it.

---

### Post by nnjond on 2010-07-13
Thanks for your interest, but that ddoesn't seem to do it.

---

### Post by Rubi1200 on 2010-07-13
Could you please post the output of

```
cat /etc/fstab
```

---

### Post by nnjond on 2010-07-13
nnjond@nnjond-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3c30ba43-6de6-4e68-856b-e5495254bbfa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2c3e1b82-4ea9-4e53-82ab-718d9d6e465f none            swap    sw              0       0
nnjond@nnjond-desktop:~$

---

### Post by YesWeCan on 2010-07-13
More info needed. Like what format is it and what happened between the time it was working and now?
It looks like it isn't mounted for some reason. Try searching this forum for how to mount disk drives. You should be able to manually mount it to confirm your files are still there. You then have to figure out why it doesn't auto-mount when connected. Tread carefully with Gparted - you can easily wipe your drive.

---

### Post by nnjond on 2010-07-13
Thanks again.


I used a live cd to copy across files from hdd a, to hdd b. with sudo privlliges, and they seem to have arrived. The format on hdd b was not  a Fat, it was Ex 4, or ntfs I'm not sure if i can tell it showed up in fstab. Please tell me how i might manually mount this hdd b.

I now think i didn't partition it. only formatted.

---

### Post by YesWeCan on 2010-07-13
/dev/sdc is the drive we are talking about, right? In your post #1 there is no line under the last line "Device Boot Start End Blocks Id System". Is this a cut & paste omission or did fdisk really not show anything?
You can see for /dev/sda that the partitions are described.

---

### Post by nnjond on 2010-07-13
That's the whole of the output for fdsk -l  the 250 gb hdd is the one in question

---

### Post by YesWeCan on 2010-07-13
Well, fdisk cannot find a partition on /dev/sdc. From your first post Gparted cannot either. So it is a pretty safe bet that it has no valid partitions. It seems no files can be accessed on that disk.

This begs the question: what happened when you did the original file copy?
Either sdc had a partition and then it was wiped or you accidentally copied to a different partition on a different disk or something I can't imagine happened.

If you still have the original files you will need to use Gparted to add a partition to sdc and then you will need to copy the files again.

Just one other thing: you said you copied the files using a live CD. You also have a linux OS on sda. Are these the same version of Ubuntu? Are you using the live CD to run fdisk or the sda OS?

---

### Post by nnjond on 2010-07-13
The os's are 10.04 both live and sda gpart finds the 250 gb hdd "unallocated".

Thanks again

---

