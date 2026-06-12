---
title: "Mount Disk on Startup?"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by YoungD112 on 2009-02-01
Hey guys! So my linux partition was getting full so I tried to add more space which showed up 53.7 GB Media.  This only adds to my disk when I have it mounted.  I was wondering is there a way to mount this automatically so I don't have to start it every time I get on my laptop?

---

### Post by taurus on 2009-02-01
Which partition you want to mount at boot?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by YoungD112 on 2009-02-01
Well the drive i want to mount is /dev/sda4.  Is there a way to merge /dev/sda4 and /dev/sda5 which is the main one?

---

### Post by taurus on 2009-02-01
It all depends on the layout of your harddrive.  Can you post the output of this commands from a terminal or a screenshot of gparted, showing /dev/sda?

```
sudo fdisk -l
```

---

### Post by YoungD112 on 2009-02-01
Here's what I get:
```
devin@devin-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe5b5a88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18407   147851504    7  HPFS/NTFS
/dev/sda2           24935       28850    31455270    5  Extended
/dev/sda3           28851       30401    12458407+   7  HPFS/NTFS
/dev/sda4           18408       24934    52428127+  83  Linux
/dev/sda5           24935       28683    30113811   83  Linux
/dev/sda6           28684       28850     1341396   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by taurus on 2009-02-01
I assume /dev/sda4 is just a storage while /dev/sda5 is where Ubuntu is located?

Do you still have Ubuntu LiveCD since you need to use gparted from it to resize your harddrive?

---

### Post by YoungD112 on 2009-02-01
Yes thats correct and I don't have the CD with me but I could always make another one.

---

### Post by taurus on 2009-02-01
Or you can use GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

After you boot from a LiveCD, I would like to see a screenshot of gparted showing your harddrive, /dev/sda.

And before you start resizing your harddrive, please _back up_ your important files first just in case.

---

### Post by YoungD112 on 2009-02-01
The LiveCD just takes me to a blank screen eventually and I never get to anything useful to me.  Heres a screen shot of GParted without the CD though.

---

### Post by taurus on 2009-02-01
When you first boot Ubuntu LiveCD, press F4 at the menu and pick the safe graphic mode.  See if it boots.

Otherwise, you can try the GParted LiveCD.  The reason is you cannot resize your partition, especially /dev/sda5, while it is in used.  Therefore, you have to do it from a LiveCD.

Assuming one of the LiveCDs works, make sure the swap partition, /dev/sda6, is not mounted.  You can unmount it from gparted.  Then, delete /dev/sda4 and expand the extended partition, /dev/sda2, to take up the unallocated space.  Now, expand /dev/sda5 to take up that new space.  Save the changes and that should do it.

---

### Post by YoungD112 on 2009-02-01
Thanks! I did everything you said and it worked flawlessly.

---

### Post by Nixie Pixel on 2009-02-02
Using the info listed in the thread above I installed NTFS-config to automatically mount my NTFS hard drives.  Unfortunately I messed up in naming the mount point of one of my NTFS drives, but couldn't find out how to rename that mounting.  So I added an entry manually to /etc/fstab for the drive, but it didn't work.  

I ended up uninstalling NTFS-config but I am still having problems because now I "am not privileged" to mount the drive.

So it appears that NTFS-config left something behind that I can't see?

My fdisk -l and mount -l entries (please note I am also trying to mount my ext3 /dev/sdb partition, but I wasn't sure if I should use /dev/sdb2 or /dev/sdb5 - how do I know that? - and I think I messed up the fstab entry):
```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb978e9cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223        9039    30660052+   5  Extended
/dev/sda5            8542        9039     4000185   82  Linux swap / Solaris
/dev/sda6            5223        7323    16876219+  83  Linux
/dev/sda7            7324        8540     9775521   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa73fa73

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15298   122881153+   7  HPFS/NTFS
/dev/sdb2           15299       60801   365502847+   5  Extended
/dev/sdb5           15299       60801   365502816   83  Linux
```

```
/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro) []
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-6-generic/volatile type tmpfs (rw,mode=755)
/dev/sda7 on /home type ext4 (rw,relatime) []
/dev/sdb1 on /media/NTFS_Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) [NTFS Data]
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/niki/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=niki)
/dev/sr1 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,utf8,user=niki) [BF2XPACK CD 1]
```

---

### Post by taurus on 2009-02-02
> **Nixie Pixel said:**
> Using the info listed in the thread above I installed NTFS-config to automatically mount my NTFS hard drives.  Unfortunately I messed up in naming the mount point of one of my NTFS drives, but couldn't find out how to rename that mounting.  So I added an entry manually to /etc/fstab for the drive, but it didn't work.  

I ended up uninstalling NTFS-config but I am still having problems because now I "am not privileged" to mount the drive.

So it appears that NTFS-config left something behind that I can't see?

My fdisk -l and mount -l entries (please note I am also trying to mount my ext3 /dev/sdb partition, but I wasn't sure if I should use /dev/sdb2 or /dev/sdb5 - how do I know that? - and I think I messed up the fstab entry):
```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb978e9cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223        9039    30660052+   5  Extended
/dev/sda5            8542        9039     4000185   82  Linux swap / Solaris
/dev/sda6            5223        7323    16876219+  83  Linux
/dev/sda7            7324        8540     9775521   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa73fa73

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15298   122881153+   7  HPFS/NTFS
/dev/sdb2           15299       60801   365502847+   5  Extended
/dev/sdb5           15299       60801   365502816   83  Linux
```

```
/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro) []
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-6-generic/volatile type tmpfs (rw,mode=755)
/dev/sda7 on /home type ext4 (rw,relatime) []
/dev/sdb1 on /media/NTFS_Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) [NTFS Data]
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/niki/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=niki)
/dev/sr1 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,utf8,user=niki) [BF2XPACK CD 1]
```

You have your /dev/sdb1 mounted to /media/NTFS_Data (your ntfs partition) but you don't have /dev/sdb5 mounted anywhere.

If you want to change a mount point, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and change it in there.  Then, don't forget to create a new mount point or the partition won't be able to mount.

```
sudo mkdir /media/*new_mountpoint*
```

---

### Post by Nixie Pixel on 2009-02-02
Yes, sorry, I meant to add this to show what I was trying to do:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=54e5c58c-b176-42c2-a97c-ef9108a6f767 / ext4 relatime,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=76cf0455-6a4d-4072-bc33-9ac1110b2b85 /home ext4 relatime 0 2
# Entry for /dev/sda5 :
UUID=8416c15f-70e1-44cd-8f08-34d47372fa8b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/xpsystem ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/NTFS_Data ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb5 /media/disk ext3 defaults,locale=en_US.UTF-8 0 0
```

---

### Post by taurus on 2009-02-02
> **Nixie Pixel said:**
> Yes, sorry, I meant to add this to show what I was trying to do:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=54e5c58c-b176-42c2-a97c-ef9108a6f767 / ext4 relatime,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=76cf0455-6a4d-4072-bc33-9ac1110b2b85 /home ext4 relatime 0 2
# Entry for /dev/sda5 :
UUID=8416c15f-70e1-44cd-8f08-34d47372fa8b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/xpsystem ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/NTFS_Data ntfs-3g defaults,locale=en_US.UTF-8 0 0
**[COLOR="Red"]/dev/sdb5 /media/disk ext3 defaults,locale=en_US.UTF-8 0 0[/COLOR]**
```

First, I would not use /media/disk as a mount point in /etc/fstab since that is usually the default mount point with automount.  Therefore, I would make the mount point for /dev/sdb5 to be something like /media/sdb5.  And besides, the entry for /dev/sdb5 should look like this.

```
/dev/sdb5   /media/sdb5   ext3   defaults   0   2
```
I assume there is a mount point for /dev/sda1, /media/xpsystem?

```
ls -la /media
```
See what happens if you try to mount that ntfs partition from a terminal?

```
sudo mount -t ntfs-3g /dev/sda1 /media/xpsystem
```

---

### Post by Nixie Pixel on 2009-02-02
Thank you, the problem was that I did not have a directory created for the mount point /media/xpsystem ...I didn't know I had to make that manually.  And thanks for the change to the parameters for the other mount.

How can I tell what parameters to use for future mountings?

(ooh, that sounds kinky! :)

Thanks!

---

### Post by taurus on 2009-02-02
You can use the entries (ext3 & ntfs) in /etc/fstab as an example now.

---

### Post by Nixie Pixel on 2009-02-03
Ok, thank you, I managed to mount /dev/sdb5 on /media/linux_data, but for some reason in Nautilus it is saying "These files are on a Picture CD." when I browse to it, and I can't manipulate files there.  I have to use sudo commands in the terminal to be able to affect that partition.

Is there any way that I can have it automatically mount as a normal hard disk drive partition?  I want to be able to transfer files in Nautilus without figuring out how to start Nautilus as root.

Thanks!

---

### Post by taurus on 2009-02-03
> **Nixie Pixel said:**
> Ok, thank you, I managed to mount /dev/sdb5 on /media/linux_data, but for some reason in Nautilus it is saying "These files are on a Picture CD." when I browse to it, and I can't manipulate files there.  I have to use sudo commands in the terminal to be able to affect that partition.

Is there any way that I can have it automatically mount as a normal hard disk drive partition?  I want to be able to transfer files in Nautilus without figuring out how to start Nautilus as root.

Thanks!

You can change the ownership of /media/linux_data from root to your login name so you can have full access (read & write) to it without using sudo or gksudo.  Assuming your login name is nixie, you could do something like

```
sudo chown -R nixie:nixie /media/linux_data
ls -la /media
```

---

### Post by Nixie Pixel on 2009-02-03
Thank you!  I only have to do this once, not every time it boots?

Edit:  It still says "these files are on a Picture CD," do you know why that is?  It only says this for my ext3 mount, not my NTFS mounts...

---

### Post by taurus on 2009-02-03
> **Nixie Pixel said:**
> Thank you!  I only have to do this once, not every time it boots?

You don't have to change the ownership everytime you boot.

> Edit:  It still says "_these files are on a Picture CD_," do you know why that is?  It only says this for my ext3 mount, not my NTFS mounts...

Can you post your /etc/fstab again?

```
cat /etc/fstab
```
Perhaps that is the label of that ext3 partition?

---

### Post by Nixie Pixel on 2009-02-03
Here is my fstab entry:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=54e5c58c-b176-42c2-a97c-ef9108a6f767 / ext4 relatime,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=76cf0455-6a4d-4072-bc33-9ac1110b2b85 /home ext4 relatime 0 2
# Entry for /dev/sda5 :
UUID=8416c15f-70e1-44cd-8f08-34d47372fa8b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/xpsystem ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/NTFS_Data ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb5   /media/linux_data   ext3   defaults   0   2
```

---

### Post by taurus on 2009-02-03
So the writing for the icon or under the icon (/dev/sdb5) on your desktop says that, "these files are on a Picture CD"?

---

### Post by Nixie Pixel on 2009-02-03
This is in Nautilus, sorry:

---

### Post by physeetcosmo on 2009-02-04
> **taurus said:**
> Which partition you want to mount at boot?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

tarus - 

Thanks for the code, i couldn't remember the blkid command to list the UUID of each disk. Changed my fstab file and now it auto mounts!

:p

---

### Post by aquavitae on 2009-02-18
Not sure if you're still looking for a way to deal with the picture cd, but I found an answer in [another thread]("http://ubuntuforums.org/showthread.php?t=967331").  I've got the same problem!  It seems it happens with you have a "Pictures" folder in the root of a drive. Rename it to something else and it should stop.  I havent' tested it yet, so I can't confirm it, but it looks like it worked for someone.

---

### Post by Nixie Pixel on 2009-02-22
> **aquavitae said:**
> Not sure if you're still looking for a way to deal with the picture cd, but I found an answer in [another thread]("http://ubuntuforums.org/showthread.php?t=967331").  I've got the same problem!  It seems it happens with you have a "Pictures" folder in the root of a drive. Rename it to something else and it should stop.  I havent' tested it yet, so I can't confirm it, but it looks like it worked for someone.

Thank you!  I tried that solution and it worked!

---

