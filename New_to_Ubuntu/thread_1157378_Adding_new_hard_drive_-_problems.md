---
title: "Adding new hard drive - problems"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by craig100 on 2009-05-12
System: quad core, 3 x 320GB HDD's, 4GB RAM.  Ubuntu 9.04 on drive sdb.  Decided to remove WinXP from sda. Using GParted, successfully partitioned sda1 as ext4 to the full size of the drive.

Created a subdirectory as a mount point at /mnt/DATA

Mounted in terminal using sudo mount /dev/sda1 /mnt/DATA

Reported correctly in mount and fdisk readouts.

Modified /etc/fstab to make disk mount at start up as below:-

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sdb1 during installation
UUID=d8faab01-393a-4095-b01c-cca07b4558c5  /               ext4         relatime,errors=remount-ro  0  1  
# swap was on /dev/sdb5 during installation
UUID=2a2f3739-3b7f-4dd7-9a26-b721a6b0a9f0  none            swap         relatime,errors=remount-ro  0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0
/dev/sda1				   /mnt/DATA	   ext4		defaults		    0  2   

Problem is that when viewed in Nautilus all I see at the mount point is /mnt/DATA/lost+found/(Empty)

What have I done wrong/missed?

Any advice would be appreciated.

Craig

---

### Post by whoop on 2009-05-12
What is the UUID?
```

sudo blkid

```

---

### Post by Cheesemill on 2009-05-12
If the drive has been newly formatted then you will only see a lost+found folder.  What were you expecting to see?

Post the results of
```
fdisk -l
```
and
```
mount
```


Cheesemill


Edit:
> **craig100 said:**
> Reported correctly in mount and fdisk readouts.
I missed this bit, sorry :)

---

### Post by Shazaam on 2009-05-12
Here is a page concerning that folder...
[https://answers.launchpad.net/ubuntu/+question/8373](https://answers.launchpad.net/ubuntu/+question/8373)

---

### Post by Cheesemill on 2009-05-12
You can also do a
```
df -h
```
to see available space on all mounted filesystems.

Cheesemill

---

### Post by craig100 on 2009-05-12
Hi,

Thanks for the quick replies:-

The UUID is:-
/dev/sda1: LABEL="data1" UUID="56b22a4b-d710-4ffc-bd5e-0a6d77f593f5" TYPE="ext4"


The output for mount is:-
/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro)
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
/dev/sda1 on /mnt/DATA type ext4 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/craig/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=craig)
/dev/sdd1 on /media/TIUCL2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


The output for fdisk -l is:-
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec98ec98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8101e04b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37811   303716826   83  Linux
/dev/sdb2           37812       38913     8851815    5  Extended
/dev/sdb5           37812       38913     8851783+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8047970f

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc1c3c8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

Yes, I'd already seen that link ([https://answers.launchpad.net/ubuntu/+question/8373](https://answers.launchpad.net/ubuntu/+question/8373)) which is what concerned me. All I expected to see was "empty" ready for me to copy files to it.

The df -h output is:-
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             286G   73G  199G  27% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  340K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  192K  1.5G   1% /dev
tmpfs                 1.5G  752K  1.5G   1% /dev/shm
lrm                   1.5G  2.7M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             294G  191M  279G   1% /mnt/DATA
/dev/sdd1             466G   86G  381G  19% /media/TIUCL2

So, what can I divine from the above? Have I done something wrong or missed something vital? Why isn't the drive ready for use or is it?

Regards,

Craig

---

### Post by Cheesemill on 2009-05-12
Every thing looks fine to me, you've got 295GB of free space on that partition; Ubuntu always creates a lost+found folder in any newly formated file system.  What made you think there was something wrong?

Cheesemill

---

### Post by craig100 on 2009-05-12
Because if I try to copy a file to the drive I get the "Error while copying xxxxx" alert "Error opeing file /mnt/xxxxx:permission denied".  Something's up somewhwhere. Don't forget, This is in the "Absolute Beginner" section, I've never added a disk before. I assumed it would pretty much work out of the box. Probably an old Windows habit, lol.

---

### Post by dark_harmonics on 2009-05-12
> **craig100 said:**
> Because if I try to copy a file to the drive I get the "Error while copying xxxxx" alert "Error opeing file /mnt/xxxxx:permission denied".  Something's up somewhwhere. Don't forget, This is in the "Absolute Beginner" section, I've never added a disk before. I assumed it would pretty much work out of the box. Probably an old Windows habit, lol.


Craig its likely that you dont have permissions to write that directory. Take ownership with

sudo chown -hR username directory

Don't get discouraged!

---

### Post by craig100 on 2009-05-13
Thanks everyone. The new disk is now working and accessbile, and I've learnt a lot for next time.  Just neeed to place my "home" directory on it now and that'll be it.  I think I've seen a few tutorials for that somewhere:)

Regards,

Craig

---

