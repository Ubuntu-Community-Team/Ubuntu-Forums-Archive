---
title: "ownership/permissions Problem"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by nnjond on 2011-04-17
Hi,

My Ubuntu os is freshly installed and I haven't tried to alter the permisions. -But I am not permited to edit my data files (not sw) on a second physical hdd as this was established in another setup.

The procedure below seems to succeed except when I open an .odt doc on the drive in question it is read only and -'is locked for editing by yourself on a different system'


```
nnjond@Den-GeForce6100PM-M2:~$ sudo fdisk -l

Disk /dev/sdb: 2023 MB, 2023751680 bytes
255 heads, 63 sectors/track, 246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000078f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         246     1975963+   b  W95 FAT32

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cedbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7725    62048092+  83  Linux
/dev/sda2            7725       30402   182149121    5  Extended
/dev/sda5           30020       30402     3068928   82  Linux swap / Solaris
/dev/sda6           15234       29669   115948544   83  Linux
/dev/sda7           29669       30019     2812928   82  Linux swap / Solaris
/dev/sda8            7725       14922    57807872   83  Linux
/dev/sda9           14922       15233     2500608   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea57a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976760832   83  Linux
nnjond@Den-GeForce6100PM-M2:~$ sudo chown -R nnjond /media/sdb1
chown: cannot access `/media/sdb1': No such file or directory
nnjond@Den-GeForce6100PM-M2:~$ sudo chown -R nnjond /dev/sdb1
nnjond@Den-GeForce6100PM-M2:~$ 

```

---

### Post by Paqman on 2011-04-17
Your secondary drive is formatted FAT32, so you won't be able to set permissions on its filesystem (FAT32 doesn't allow this)

What you'll have to do is edit the entry in /etc/fstab that mounts this drive. You can edit fstab by:
```
gksudo gedit /etc/fstab
```

Find the line that mounts /dev/sdb and edit the options so that it mounts as owned by your user number (you can find that in Users & Groups, it's probably 1000).

Your fstab entry should look something like:
```
/dev/sdb1 /mount/point vfat uid=1000 0 0
```

 If you want it to be available for multiple users you can create a group and mount the drive as owned by that group (use gid instead of uid in the fstab entry)

---

### Post by nnjond on 2011-04-17
Thanks for your help. gksudo gedit /etc/fstab returns a what looks like a mess to me and I would like more advice on how to edit it.


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=a3ffe353-a16a-48ba-b3bd-0ee0504760e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=bcd246b0-391f-4031-899d-a18966087b0c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Paqman on 2011-04-17
Ok, if that's the whole file, then you're obviously not mounting this drive automatically at boot. If you want to set permissions on it you'll need to mount it automatically:

Create a mount point:
```
sudo mkdir /mount/point
```

If you choose /media/something for this mount point, it will show on the desktop all the time, if you don't want that create the mount point in /mnt instead.

Add the entry I gave above to /etc/fstab as a new line at the bottom. Then save it and mount the new drive with:
```
sudo mount -a
```

---

### Post by nnjond on 2011-04-17
Sorry; it seems I have not followed your instructions as I should...


:~$ mkdir /media/571332a7-9eb6-45fb-9259-197d99332851mkdir: cannot create directory `/media/571332a7-9eb6-45fb-9259-197d99332851': File exists
nnjond@Den-GeForce6100PM-M2:~$ 


sudo mkdir /media/store


gksudo gedit /etc/fstab


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=a3ffe353-a16a-48ba-b3bd-0ee0504760e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=bcd246b0-391f-4031-899d-a18966087b0c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sdb1 /media/store vfat uid=1000 0 0


sudo mount -a

drive is not mounted, nor at reboot.

---

### Post by Paqman on 2011-04-17
Ah, the # at the start of some lines in that file means those lines are just comments, so the system ignores them. Remove the # at the start of the line you added and try again.

---

### Post by nnjond on 2011-04-17
I don't understand why it should find it? Just by making a dir called store? The drive is in /media/ , not /media/store/ ?

fstab now looks like this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=a3ffe353-a16a-48ba-b3bd-0ee0504760e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=bcd246b0-391f-4031-899d-a18966087b0c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/store vfat uid=1000 0 0

---

### Post by Paqman on 2011-04-17
> **nnjond said:**
> I don't understand why it should find it? Just by making a dir called store? The drive is in /media/ , not /media/store/ ?


The entry in /etc/fstab tells the system to take the partition at /dev/sdb1 and mount it at /media/store, that it's FAT32 and that all the files should be owned by user id 1000.

---

### Post by nnjond on 2011-04-17
Thanks for bearing with me, But there has been a mix up I've just noticed. Your advice has led me establish my 2gb pen drive in /media/store, which already appeared on my desktop at boot. 

I want to establish full access to my ancillary 1Tb internal drive. I can manually mount this but, as I said, It wont give me full editing permissions. It seems I need to locate this using Bash and then modify the line i added to fstab accordingly.

---

### Post by Paqman on 2011-04-17
Ah, right, I assume the /dev/sdb shown above was your second hard drive. My mistake, it looks like its the /dev/sdd1, which is not mounted automatically.

Since it's a Linux filesystem you can simply alter the permissions and ownership of any file on it. To take ownership of all files on it:
```
sudo chown -R username:username /mount/point
```

You can also add an entry to fstab like:
```
/dev/sdd1 /media/store ext4 defaults 0 0
```
...and it will be automatically mounted at boot time.

---

### Post by Paqman on 2011-04-17
/disregard

---

### Post by nnjond on 2011-04-17
I don't understand your last post?

I have already followed your advice. On reboot I receive the mssge:

The diskdrive for media/store is not present or ready. Press S to skip.

I still don't have edditing permisions.

---

### Post by Paqman on 2011-04-17
> **nnjond said:**
> I don't understand your last post?

For some reason the forum double-posted, so I deleted it.

> 
I have already followed your advice. On reboot I receive the mssge:

The diskdrive for media/store is not present or ready. Press S to skip.

I still don't have edditing permisions.

Ok. Is the drive actually mounted? To what mount point? When you right click on it and go to "permissions" who owns it?

---

### Post by nnjond on 2011-04-17
/media/571332...

The permissions of "571332..." could not be determined.

---

