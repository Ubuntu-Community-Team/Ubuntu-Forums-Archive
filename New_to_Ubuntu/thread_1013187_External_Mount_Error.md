---
title: "External Mount Error"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by hismindkills on 2008-12-16
I tried plugging my WD external drive into my laptop (running Ubuntu 8.10), and when I went to access one of the files, I wasn't able to find the directory and when I went to open the drive itself, I was given the error message "Unable to mount location; cannot mount file" Nothing else.

I tried looking at the mount commands in the terminal, but I'm new to Ubuntu so I wasn't quite sure what I was looking at for a while.

---

### Post by Michael.Godawski on 2008-12-16
hi hismindkills, 

can you please post the outputs of these terminal commands, while the wd drive is plugged in:

```
sudo fdisk -l
mount
```

---

### Post by bumanie on 2008-12-16
What filesystem does the have on it? NTFS; FAT32; EXT3 or something else?

---

### Post by hismindkills on 2008-12-16
> **Michael.Godawski said:**
> hi hismindkills, 

can you please post the outputs of these terminal commands, while the wd drive is plugged in:

```
sudo fdisk -l
mount
```

```

mhundley@mhundley-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x475a4759

   Device Boot      Start         End      Blocks   Id  System
mhundley@mhundley-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mhundley/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mhundley)
mhundley@mhundley-laptop:~$ 
```

---

### Post by taurus on 2008-12-16
You need to use gparted, create a partition on that new harddrive (/dev/sdb1), and format it to whatever filesystem you want.

```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by Michael.Godawski on 2008-12-16
> Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x475a4759

   Device Boot      Start         End      Blocks   Id  SystemIs this the whole output of the first command? It seems there is something missing...
or you need to create a new partition on it...
see taurus' post ;)

---

### Post by hismindkills on 2008-12-16
> **bumanie said:**
> What filesystem does the have on it? NTFS; FAT32; EXT3 or something else?


Not quite sure.  It's an older drive from Western Digital (about 2 years old).  I poked around their website for a while, but they didn't seem to have anything up about what filesystem it's running.

---

### Post by taurus on 2008-12-16
> **Michael.Godawski said:**
> Is this the whole output of the first command? It seems there is something missing...

Actually, there wouldn't be anything missing.  It's probably new drive so he/she needs to create a partition and format it first before he/she can write or use it.

---

### Post by xjcannonx on 2008-12-16
Was this drive previously connected to windows OS? if it was then this is probably your problem from my ekperience. If it wasnt (removed safely) or whatever from windows then it wont be able to be mounted

---

### Post by Michael.Godawski on 2008-12-16
> Actually, there wouldn't be anything missing. It's probably new drive so he/she needs to create a partition and format it first before he/she can write or use it.Thx Taurus. Yes you are right. It is getting late here and my braincells start to cry for sleep. Time for others stand guard for the night. :p Good night.

---

### Post by bumanie on 2008-12-16
Plug it in, then go to Applications --> Accessories --> Terminal and input the code > sudo apt-get install gpartedThen go to System --> Administration --> Partition editor and open it. You should see the external drive as being unallocated. Then click on 'new' and format the drive to whatever filesystem you want. You will have to unmount the drive first.

---

### Post by hismindkills on 2008-12-16
> **taurus said:**
> You need to use gparted, create a partition on that new harddrive (/dev/sdb1), and format it to whatever filesystem you want.

```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```


I went through and reformatted it, rebooted and remounted the device, but now when I try to copy files on to it, I get a "Permission denied" error message.  How do I change the permissions?

---

### Post by taurus on 2008-12-16
What filesystem did you use and where do you mount it?

```
sudo fdisk -l
cat /etc/fstab
id
```

---

### Post by kansasnoob on 2008-12-16
> **hismindkills said:**
> I tried plugging my WD external drive into my laptop (running Ubuntu 8.10), and when I went to access one of the files, I wasn't able to find the directory and when I went to open the drive itself, I was given the error message "Unable to mount location; cannot mount file" Nothing else.

I tried looking at the mount commands in the terminal, but I'm new to Ubuntu so I wasn't quite sure what I was looking at for a while.


**EVERYONE** should pay attention here! The op said, "when I went to access one of the files", so this is a drive that already exists! So let's make it simple:

Install pmount either from synaptic or:

```
sudo apt-get install pmount
```

If the drive has ntfs partitions also install ntfsprogs (ntfs-config is an option), both are in synaptic or:

```
sudo apt-get install ntfsprogs
```

Now, ntfsprogs provides excellent read & write support to all ntfs partitions so you can destroy either XP or Vista program files if you choose to!

---

### Post by hismindkills on 2008-12-16
> **taurus said:**
> What filesystem did you use and where do you mount it?

```
sudo fdisk -l
cat /etc/fstab
id
```

Here's the output I get from those commands:

```
mhundley@mhundley-laptop:~$ sudo fdisk -l
[sudo] password for mhundley: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris
   

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x475a4759

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
mhundley@mhundley-laptop:~$ 
mhundley@mhundley-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=04131839-f922-4c7a-8d3f-5b378905ac9a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4b9a06b2-d379-45ab-856b-f21471a0315e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
mhundley@mhundley-laptop:~$ id
uid=1000(mhundley) gid=1000(mhundley) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(mhundley)
mhundley@mhundley-laptop:~$ 

```

---

### Post by kansasnoob on 2008-12-16
Just FYI from synaptic:

> pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.

And:

> This is a set of tools targeted for people interested in working
with the NTFS support in the Linux kernel and using it.  The
following utilities are included:

ntfsfix - Fix common filesystem errors and force Windows to check NTFS.

mkntfs - Format a partition with an NTFS filesystem, optionally bootable.

ntfsinfo - Show some information about an NTFS partition or one of the
files or directories within it.

ntfslabel - Show, or set, an NTFS partition's volume label.

ntfsresize - Resize an NTFS partition without losing data.

ntfsundelete - Recover deleted files from an NTFS partition.

ntfscluster - Locate the owner of any given sector or cluster on an NTFS
partition.

ntfscat - Concatenate files and print them on the standard output
(without mounting the partition).

ntfsls - List directory contents on an NTFS filesystem (without
mounting).

ntfscp - Overwrite files on an NTFS partition.

ntfsclone - Efficiently clone an NTFS filesystem or a part of it.

ntfsmount - Mount an NTFS partition from user-space using libntfs and FUSE.

ntfsdecrypt - Decrypt NTFS-encrypted files (NOT INCLUDED).

ntfscmp - Compare two NTFS volumes and tell the differences.

Canonical provides critical updates for ntfsprogs.

---

### Post by kansasnoob on 2008-12-16
I should however add that you must always remember to unmount an external drive before unplugging it!

Otherwise you'll be really mad at yourself after spending an hour or more remounting the device and you could lose data!

---

### Post by taurus on 2008-12-16
If you already mounted /dev/sdb1, unmount it.

```
sudo umount /dev/sdb1
```
Then, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   2
```
Save it and close down gedit window.  Now, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```
If you want to write to /media/sdb1 without using sudo or gksudo, then you need to change the ownership of /media/sdb1 from root to your login name, mhundley.

```
sudo chown -R mhundley:mhundley /media/sdb1
ls -la /media
```

---

### Post by taurus on 2008-12-16
> **kansasnoob said:**
> **EVERYONE** should pay attention here! The op said, "when I went to access one of the files", so this is a drive that already exists! So let's make it simple:

Install pmount either from synaptic or:

```
sudo apt-get install pmount
```

If the drive has ntfs partitions also install ntfsprogs (ntfs-config is an option), both are in synaptic or:

```
sudo apt-get install ntfsprogs
```

Now, ntfsprogs provides excellent read & write support to all ntfs partitions so you can destroy either XP or Vista program files if you choose to!

BUT it is ext3 (/dev/sdb1) so ntfsprogs is useless...

---

