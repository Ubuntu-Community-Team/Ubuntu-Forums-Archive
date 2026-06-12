---
title: "How do I read my shared patition (FAT32) from Ubuntu? (Vista-Ubuntu 10.10 Dual boot)"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by flee0308 on 2011-02-17
As above. I partitioned my drive to have a logical 30Gb FAT32 Shared partition.

In Windows vista, I am able to read/write to the partition, and is listed as a J Drive.

However, I am unable to find this partition on Ubuntu.

During the partitioning process, I set the partition to /windows. Does this have anything with Ubuntu being unable to find the partition? If so, how do I solve it?

One more thing. I heard that the maximum size for a FAT32 partition is 30Gb. Is that true?

---

### Post by mastablasta on 2011-02-17
Go to places and it should be there (as will any NTFS partitions). They won't be named C:, D: (this is how MSDOS based system mark their drives. instead their label will show up or maybe only (in your case) 30GB file system or something like that.

---

### Post by seawolf167 on 2011-02-17
32GB was the limit for formatting FAT32 on an XP box, even though it could mount larger drives. The suggestion back in the day was to use the "new" NTFS format.

Like mastablasta said, you should be able to find the drive under "Places", if not you cannot, please post the output of 

```
mount
```and the contents of

```
vi /etc/fstab
```so we can see what your computer has mounted and is set to automatically mount

---

### Post by hansolo4949 on 2011-02-17
yes, you should be able to see it just fine, but it is called differently in Ubuntu, as mastablasta said. Open up some if the drives that seem likely to have your data on them, and eventually you will find the ine that has your data in it:p.

---

### Post by Paqman on 2011-02-17
> **seawolf167 said:**
> 
```
vi /etc/fstab
```

You might find:
```
gedit /etc/fstab
```
a lot easier to use than vi

---

### Post by seawolf167 on 2011-02-17
> **Paqman said:**
> You might find:
```
gedit /etc/fstab
```a lot easier to use than vi


**Never!** Wait, yea you're right... I'll change that in subsequent posts. Thanks

---

### Post by quadproc on 2011-02-17
> **flee0308 said:**
> As above. I partitioned my drive to have a logical 30Gb FAT32 Shared partition.

In Windows vista, I am able to read/write to the partition, and is listed as a J Drive.

However, I am unable to find this partition on Ubuntu.

Did you mount the new partition?  If not, then it will not be accessible to most things.  You can either mount partitions manually or you can include them in your /etc/fstab file for automounting at startup time.  Or, the disk utility has a place to mount a partition.
> 
During the partitioning process, I set the partition to /windows.
Do you mean that you made its label "/windows"?

quadproc

---

### Post by flee0308 on 2011-02-19
> **mastablasta said:**
> Go to places and it should be there (as will any NTFS partitions). They won't be named C:, D: (this is how MSDOS based system mark their drives. instead their label will show up or maybe only (in your case) 30GB file system or something like that.

Nope, I checked every folder. IT is just not there.

> **seawolf167 said:**
> 32GB was the limit for formatting FAT32 on an XP box, even though it could mount larger drives. The suggestion back in the day was to use the "new" NTFS format.

Like mastablasta said, you should be able to find the drive under "Places", if not you cannot, please post the output of 

```
mount
```and the contents of

```
vi /etc/fstab
```so we can see what your computer has mounted and is set to automatically mount

> **Paqman said:**
> You might find:
```
gedit /etc/fstab
```
a lot easier to use than vi
For mount,I got

```

/dev/sda3 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda6 on /tmp type ext4 (rw,commit=0)
/dev/sda7 on /var type ext4 (rw,commit=0)
/dev/sda9 on /home type ext4 (rw,commit=0)
/dev/sda8 on /windows type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/frank/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=frank)
/dev/sdf1 on /media/My Passport type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda1 on /media/COMPAQ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2 on /media/FACTORY_IMAGE type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```


For vi /etc/fstab, I got

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e0177bfc-3297-4152-a13d-034bea0c372a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=e3958bd4-13a6-49f0-b76a-3d046466e915 /home           ext4    defaults        0       2
# /tmp was on /dev/sda6 during installation
UUID=bb0d0d04-68ac-4d76-9b20-1d6e71e6e36e /tmp            ext4    defaults        0       2
# /var was on /dev/sda7 during installation
UUID=71adb42b-03c9-4673-8054-b25e6a1286a1 /var            ext4    defaults        0       2
# /windows was on /dev/sda8 during installation
UUID=53F2-76B1  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=d2c39148-98ee-4103-aac9-3abd69367154 none            swap    sw              0       0
~                                                                               
~                              

```

For gedit /etc/fstab, I got

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e0177bfc-3297-4152-a13d-034bea0c372a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=e3958bd4-13a6-49f0-b76a-3d046466e915 /home           ext4    defaults        0       2
# /tmp was on /dev/sda6 during installation
UUID=bb0d0d04-68ac-4d76-9b20-1d6e71e6e36e /tmp            ext4    defaults        0       2
# /var was on /dev/sda7 during installation
UUID=71adb42b-03c9-4673-8054-b25e6a1286a1 /var            ext4    defaults        0       2
# /windows was on /dev/sda8 during installation
UUID=53F2-76B1  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=d2c39148-98ee-4103-aac9-3abd69367154 none            swap    sw              0       0

```

> **quadproc said:**
> Did you mount the new partition?  If not, then it will not be accessible to most things.  You can either mount partitions manually or you can include them in your /etc/fstab file for automounting at startup time.  Or, the disk utility has a place to mount a partition.
Do you mean that you made its label "/windows"?

quadproc

Yeah I made its label "windows".

---

### Post by flee0308 on 2011-02-19
bump.

---

### Post by Chronon on 2011-02-19
It looks like it's mounted at /windows (/dev/sda8).

---

### Post by flee0308 on 2011-02-20
> **Chronon said:**
> It looks like it's mounted at /windows (/dev/sda8).

Indeed it is. But how do I access it?

---

### Post by flee0308 on 2011-02-20
bump

---

### Post by candtalan on 2011-02-20
> **flee0308 said:**
> Indeed it is. But how do I access it?

I would expect to see it listed in the top menus (applications, places, system). Using the Places dropdown, it will hopefully be listed. If so then a single left mouse click will open it in (nautilus) file manager.

Alternatively open your home folder (places>home folder) and verify that view>side pane is enabled, you should see the folder listed at the left hand side pane. To open it in file manager, a left mouse click.

hth

---

### Post by Morbius1 on 2011-02-20
> **flee0308 said:**
> Indeed it is. But how do I access it?
Nautilus > File System > windows  

If you access it often you can create a bookmark in Nautilus so it shows up in the left side panel under Places.

---

### Post by flee0308 on 2011-02-20
> **Morbius1 said:**
> Nautilus > File System > windows  

If you access it often you can create a bookmark in Nautilus so it shows up in the left side panel under Places.

Sorry, but what's Nautilus?

---

### Post by Morbius1 on 2011-02-20
Your Home folder. Places > Home Folder

---

### Post by flee0308 on 2011-02-20
> **Morbius1 said:**
> Your Home folder. Places > Home Folder

I see. But when I go there, I do not see a nautilus folder. Do I need to enter as root or something?

---

### Post by Morbius1 on 2011-02-20
Nautilus is the name of the File Manager in Gnome. When you launch your Home Folder you are launching Nautilus. Once your Home Folder opens just go to "File System" and then "windows."

---

### Post by flee0308 on 2011-02-20
> **Morbius1 said:**
> Nautilus is the name of the File Manager in Gnome. When you launch your Home Folder you are launching Nautilus. Once your Home Folder opens just go to "File System" and then "windows."

Ah, I see. But I still don't see "File System". When I open the Home Folder, I see:

Desktop
Documents
Downloads
Music
Pictures
Public
Templates
Videos
Examples

---

### Post by Morbius1 on 2011-02-20
Open a terminal and type:
```
nautilus /windows
```

---

### Post by flee0308 on 2011-02-20
> **Morbius1 said:**
> Open a terminal and type:
```
nautilus /windows
```

Thanks bro, I found it. One final question: How can I create a bookmark?

EDIT: haha, found that too. Apparently dragging it to the left panel is enough. Thanks alot!

---

### Post by Morbius1 on 2011-02-20
Once Nautilus opens to /windows go to the top bar of Nautilus and select "Bookmarks". Then select "Add Bookmark".

---

### Post by candtalan on 2011-02-20
> **flee0308 said:**
> Ah, I see. But I still don't see "File System". When I open the Home Folder, I see:

Desktop
Documents
Downloads
Music
Pictures
Public
Templates
Videos
Examples

as my earlier post:
open your home folder (places>home folder) and verify that view>side pane is enabled, you should see the folder listed at the left hand side pane. To open it in file manager, a left mouse click

---

### Post by Morbius1 on 2011-02-20
> **candtalan said:**
> as my earlier post:
open your home folder (places>home folder) and verify that view>side pane is enabled, you should see the folder listed at the left hand side pane. 
Actually you won't - not unless the mount point is in /home/username or in /media. If it's in /mnt or anywhere off the root ("/") directory then it will not show up unless you create a bookmark.

---

