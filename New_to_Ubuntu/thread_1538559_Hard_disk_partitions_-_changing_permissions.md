---
title: "Hard disk partitions - changing permissions"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Fifthmarch on 2010-07-25
I recently partitioned my hard disk. I am not able to add any files/folders to the new partitions. I checked the permissions and it says that only root can write to the partitions. How do I change the settings?


Thanks!

---

### Post by Gone fishing on 2010-07-25
If you want partitions mounted at boot and the permissions set so that all users can write to say an ntfs partition you need to change the fstab file. Have a look at [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) there is also a gui to help mount manager

---

### Post by Fifthmarch on 2010-07-28
I tried changing the fstab file, but then my system didn't boot, and I had to use a livecd to revert it. 

This is the fstab file:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=24cd06c6-69cf-48a1-8485-37abe538282e /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda11 during installation
UUID=7a2f0ddf-53bb-486c-a9df-48fe591a397e /home           ext3    relatime        0       2
# /home/windows -- 
UUID=99e6dc05-35a9-419a-9601-38fa51842b07 /home/#####/windows ext3 relatime       0       2
# swap was on /dev/sda10 during installation
UUID=9cbd0fc8-b113-43d2-9eb6-612edb69dcbf none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

All I can see here are the /, /home, /home/windows, and swap partitions. All these are in my first hard disk. Where are the partitions from my second hard disk, and how do I add them here? I can mount and unmount them, I am just not able to write to the new partitions. 

Any help is appreciated, I'm getting quite a headache.

---

### Post by Zimmer on 2010-07-28
> **Fifthmarch said:**
> I recently partitioned my hard disk. I am not able to add any files/folders to the new partitions. I checked the permissions and it says that only root can write to the partitions. How do I change the settings?


Thanks!
I will assume from your 2nd post that we are talking about an additional disk , not the disk your Ubuntu installation is on??

Quick way (that I know ) for convenience sake is to add DISK MOUNTER to your panel for ease of mounting other disks when you want...

Then from terminal  type  gksudo nautilus  which will bring up nautilus as root.

Navigate to required partition and create a folder on it, then right click on the folder and change permissions so that your user (or all users ) can read/write to that folder....
..............
There may be 'proper' way to do this to the whole partition with chown  but I will have to go and search for that again as I did not write it down when I last found it!!!

Actually, I do not think chown will help, I am thinking that the disk will need to be mounted with permissions applied in the mount statement first...

I think I will investigate further... but I will continue doing what I have already explained above ,for the time being... (it works for me !)

---

### Post by Morbius1 on 2010-07-28
There's is not enough information in your post to answer your question.

We don't know how you formatted the new partition or where it physically is located. To answer that question please provide the output of the following command:
```
sudo blkid -c /dev/null
```This could be a very simple problem to resolve. If it's a new ext3/4 filesystem then a simple chown or chmod command will fix it. If it's a Windows filesystem ( FAT32 or NTFS ) then a new line in fstab will have to be added to assign ownership and permissions since chown or chmod will not work on Windows filesystems.

---

### Post by Fifthmarch on 2010-07-28
Here's the output of sudo blkid -c /dev/null

/dev/sda1: UUID="51c5cf5d-3d7e-46b7-b51c-8ddebf81c7dc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: LABEL="Backup" UUID="93F2-27B3" TYPE="vfat" 
/dev/sda3: LABEL="Partition 2" UUID="f26231af-d0c0-4a1e-8406-5a244bb0f6b4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: LABEL="Partition 3" UUID="ccf415c0-6ca4-4971-b335-70b38cd2e2ff" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: LABEL="NEW VOLUME" UUID="D02F-1DA2" TYPE="vfat" 
/dev/sdb6: LABEL="NEW VOLUME" UUID="E87E-EDA2" TYPE="vfat" 
/dev/sdb7: LABEL="NEW VOLUME" UUID="4C88-C3C8" TYPE="vfat" 
/dev/sdb8: UUID="99e6dc05-35a9-419a-9601-38fa51842b07" TYPE="ext3" 
/dev/sdb9: UUID="24cd06c6-69cf-48a1-8485-37abe538282e" TYPE="ext3" 
/dev/sdb10: UUID="9cbd0fc8-b113-43d2-9eb6-612edb69dcbf" TYPE="swap" 
/dev/sdb11: UUID="7a2f0ddf-53bb-486c-a9df-48fe591a397e" TYPE="ext3"

---

### Post by oldfred on 2010-07-29
After you edit fstab always run this to verify that everything is ok. It will just come back to the terminal if ok or else give error messages.

```
sudo mount -a
```

this line looks like a problem what is ###?
UUID=99e6dc05-35a9-419a-9601-38fa51842b07 /home/#####/windows ext3 relatime       0       2

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Once you have reviewed above then you can use the easier way:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by Fifthmarch on 2010-07-29
[QUOTE=oldfred;9650986]After you edit fstab always run this to verify that everything is ok. It will just come back to the terminal if ok or else give error messages.

```
sudo mount -a
```this line looks like a problem what is ###?
UUID=99e6dc05-35a9-419a-9601-38fa51842b07 /home/#####/windows ext3 relatime       0       2

/QUOTE]

That's my username - I just replaced it with #

---

### Post by Morbius1 on 2010-07-29
You actually have multiple questions here:

> I tried changing the fstab file, but then my system didn't boot, and I had to use a livecd to revert it. The fstab you published looks fine to me so if it's not booting with that fstab then I'm missing something.

> I can mount and unmount them, I am just not able to write to the new partitions. The sda2, sdb5, sdb6, sdb7 partitions will mount from nautilus with you as owner so you should be able to read and write to those without a problem

The sda1, sda3, sda4 partitions will mount from Nautilus with root as owner with full read / write permissions to root only. After the partition is mounted you can change the ownership to you by issuing the following command with this type of syntax:

```
sudo chown your_user_name /media/whatever-its-mountpoint-is
```

---

### Post by Fifthmarch on 2010-07-30
I got the mount point from Palimpsest Disk Utility- /dev/sda4 mounted on /media/Partition 3 (There IS a space before 3)

This is what I get:

xyz@xyz-desktop:~$ sudo chown xyz /media/Partition 3
chown: cannot access `/media/Partition': No such file or directory
chown: cannot access `3': No such file or directory

:oops: Someone spot what I'm doing wrong.....

BTW - the fstab file I put up is the one that works, not the one that didn't let me boot the system.

---

### Post by Morbius1 on 2010-07-30
You spotted the problem with the mountpoint yourself:
> /dev/sda4 mounted on /media/Partition 3 (There IS a space before 3)Linux hates spaces. It will deal with them but you have to take extra measures to help it deal with them. Your chown expression needs to be modified to accomodate the space:

```
sudo chown xyz /media/"Partition 3"
```

---

### Post by Fifthmarch on 2010-07-30
It works! Thanks a LOT, everyone!!!\\:D/

---

