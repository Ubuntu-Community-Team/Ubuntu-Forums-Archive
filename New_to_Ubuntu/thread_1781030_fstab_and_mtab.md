---
title: "fstab and mtab"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by VoodooLoveDog on 2011-06-12
I just recently installed two new HDs in my computer. However, I'm running into a slight problem. 

The fstab shows the following:


```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1

```

mtab shows the following:

```
/dev/sdc1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/owner/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=owner)

```

The OS is showing the two new drives on /dev/sda and /dev/sdb so when I try and mount the first volume, it gives me an error. 

What do I change? fstab to reflect the correct mount in the mtab? Do I need to do something with the grub loader?

Please advise.

---

### Post by trozamon on 2011-06-12
I think you might need to change the "dev/sda1" in the fstab file to "dev/sdc1" if I understand you're problem correctly. Don't forget to restart, and keep your LiveCD handy just in case it won't boot.

---

### Post by VoodooLoveDog on 2011-06-12
If I change fstab to /dev/sdc will that cause my system to not boot?

---

### Post by trozamon on 2011-06-12
If I understand you right, you're saying that you had an original hard drive: "dev/sda". You added two more, and "/dev/sda" got moved to "/dev/sdc", right? If that's what happened, changing the fstab file should make it work right.

I didn't really understand your description of the problem; if you could go a little more in depth, that would be great.

---

### Post by VoodooLoveDog on 2011-06-12
Yes. I added to HDs and when I ran fdisk -l I came up with the boot drive as /dev/sdc. The two new drives reported as /dev/sda and /dev/sdb. When I tried to mount the first new drive I got an error because fstab saw the boot drive as /dev/sda but mtab was reporting it as /dev/sdc. 

I was concerned that editing fstab from /dev/sda to /dev/sdc would cause a boot failure.

---

### Post by lmarmisa on 2011-06-12
I recommend to use [UUIDs]("http://en.wikipedia.org/wiki/Universally_unique_identifier").

Please, open a terminal, type these commands and post here the results:

```

sudo fdisk -l
mount
sudo blkid

```

---

### Post by trozamon on 2011-06-12
I just thought of this; how are the drives formatted?

---

### Post by VoodooLoveDog on 2011-06-12
sudo fdisk -l

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xae01ae01

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07dd07dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   42  SFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d5381

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       37434   300686336   83  Linux
/dev/sdc2           37434       38914    11882497    5  Extended
/dev/sdc5           37434       38914    11882496   82  Linux swap / Solaris

```
mount
```

/dev/sdc1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/owner/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=owner)

```
sudo blkid
```

/dev/sda1: UUID="4CB41BC2B41BAD88" TYPE="ntfs" 
/dev/sdb1: LABEL="New Volume" UUID="1828B79428B76EFE" TYPE="ntfs" 
/dev/sdc1: UUID="03fc4e19-bffd-4b3f-820b-50f4d1708ebb" TYPE="ext4" 
/dev/sdc5: UUID="52455b0b-43c8-46a9-b2f1-0d6ba66a00dc" TYPE="swap" 


```

---

### Post by lmarmisa on 2011-06-12
Thanks. Please post the result of this other command:

```

cat /etc/fstab

```

---

### Post by VoodooLoveDog on 2011-06-12
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=52455b0b-43c8-46a9-b2f1-0d6ba66a00dc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by lmarmisa on 2011-06-12
I recommend to edit the file /etc/fstab:

```

sudo gedit /etc/fstab

```

and change the line of the root partition in this way (the line is marked in blue):

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR="Blue"]UUID=03fc4e19-bffd-4b3f-820b-50f4d1708ebb / ext4 errors=remount-ro 0 1[/COLOR]
# swap was on /dev/sda5 during installation
UUID=52455b0b-43c8-46a9-b2f1-0d6ba66a00dc none swap sw 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Save & Exit.

---

### Post by VoodooLoveDog on 2011-06-12
Thanks.

---

