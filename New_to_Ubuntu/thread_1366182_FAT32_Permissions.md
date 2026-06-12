---
title: "FAT32 Permissions"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Tahakki on 2009-12-28
Hey guys.

I recently upgraded to a new computer, and after much arguing with Windows 7 managed to reduce its partition to 250GB (on our 1TB drive)(this is /dev/sda1). I then used GParted to make a 250GB partition for Ubuntu (/dev/sda2) and a 500GB storage partition (/dev/sda3). I want every user to be able to read and write to the storage partition, and I want it to be mounted on startup - but not show up on the Desktop.

Is any of this possible?

Thanks,
Tahakki

---

### Post by Primefalcon on 2009-12-28
> **Tahakki said:**
> Hey guys.

I recently upgraded to a new computer, and after much arguing with Windows 7 managed to reduce its partition to 250GB (on our 1TB drive)(this is /dev/sda1). I then used GParted to make a 250GB partition for Ubuntu (/dev/sda2) and a 500GB storage partition (/dev/sda3). I want every user to be able to read and write to the storage partition, and I want it to be mounted on startup - but not show up on the Desktop.

Is any of this possible?

Thanks,
Tahakki
sure you can tell ubuntu not to show mounted partitions/drives on the desktop by holding alt and pressing F2

type in gconf-editor and hit enter

now navigate the left hierarchy like so:

aps -> nautilus -> desktop

now in the right panel untick the option that says volumes_visible, and that's it your done, close the window, mounted drives/partitions will no longer show on your desktop, though you will still be able to access from places or computer

---

### Post by mbzn on 2009-12-28
you can mount the 500Gib as /home.

---

### Post by Primefalcon on 2009-12-28
here's a good guide for mounting as home too btw

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Tahakki on 2009-12-28
No, I can't mount it as /home, as I want settings etc to still be in Ubuntu - the Storage partition should be only for stuff I want to share, like music, videos and photos.

---

### Post by prshah on 2009-12-28
> **Tahakki said:**
> Windows 7 managed to reduce its partition to 250GB (on our 1TB drive)(this is /dev/sda1). 250GB partition for Ubuntu (/dev/sda2) and a 500GB storage partition (/dev/sda3). I want every user to be able to read and write to the storage partition

First off, I recommend you use NTFS, not FAT32 for your storage partition. Ubuntu reads/writes NTFS since 7.10 onwards.

From 8.10 onwards, Ubuntu is moving to eliminate dependence on static configuration files such as /etc/fstab and /etc/X11/xorg.conf. In this case, your NTFS partitions will be available on Ubuntu, and will automatically mount WHEN ACCESSED. This is dynamic mounting.

If you want the partition to be automatically (statically) mounted, you need to add the specific information to the /etc/fstab file. For example, you need to add an entry such as ```

#For an NTFS /FAT32 partition:  filesystem type ntfs/vfat
# /dev/sda3
[color=red]UUID=AB707BCE707F8DE8[/color] [color=blue]/media/sda3[/color]     ntfs    [color=green]defaults,umask=007,gid=46[/color] 0       0
```

In the above example (your details will differ), you can find out the correct UUID for your partition (the part in red) using the command```
sudo blkid /dev/sda3
``` (Replace sda3 with the actual partition device ID in your case).

You should also create the mount point (the part in blue)```
sudo mkdir /media/sda3
sudo chown root:plugdev /media/sda3

```

If it is NTFS, you needn't look into permissions, as long as you mount it as above.

---

### Post by Tahakki on 2009-12-28
I tried the above with the FAT32 partition, but it didn't automount, and trying to mount it gave an error message about needing to be superuser.

Is it not possible with FAT32? How reliable is Ubuntu's NTFS reading/writing?

---

### Post by prshah on 2009-12-28
> **Tahakki said:**
> 
Is it not possible with FAT32? How reliable is Ubuntu's NTFS reading/writing?

Yes it is possible with FAT32. NTFS read/write is very reliable.

Please post the following information from the terminal (Applications-Accessories-Terminal) for clues to why it didn't work:```

cat /etc/fstab
sudo blkid
mount|grep sda
groups
```

---

### Post by Tahakki on 2009-12-28
cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=23e26ca6-796d-4a61-aa82-064eec4577c0 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

sudo blkid:

```
/dev/sda1: UUID="9A78A5B178A58C97" TYPE="ntfs" 
/dev/sda2: UUID="23e26ca6-796d-4a61-aa82-064eec4577c0" TYPE="ext4" 
/dev/sda3: LABEL="Storage" UUID="4D70-93D6" TYPE="vfat" 

```

mount|grep sda:

```
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
```

groups:

```
joel adm dialout cdrom plugdev lpadmin admin sambashare
```
[B]
The above all done with no partitions mounted, including the storage one. With storage mounted (I had to enter root password), it's the following:
[/B]

cat /etc/fstab = the same

sudo blkid = the same

mount|grep sda:

```
/dev/sda3 on /media/Storage type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```

groups = the same

**Any clues?**

---

### Post by Tahakki on 2009-12-28
Bump?

---

### Post by Morbius1 on 2009-12-28
Open **Terminal**
Type **sudo mkdir /mnt/Storage**
Type **sudo su**
Type **echo "LABEL=Storage /mnt/Storage vfat utf8,umask=007,uid=1000,gid=46 0 0" >> /etc/fstab**
Type [B]sudo mount -a
[/B] 
 What should happen is this:

The mount point in /mnt will not produce an icon on the desktop
umask=007 will give the owner and group read/write access to the mountpoint
uid=1000 will make you the owner
gid=46 will make group plugdev - and all users are part of plugdev so all users will have read/write access

That's what should happen anyway.

---

### Post by Tahakki on 2009-12-28
Ah, now, that's working better. I did what you said and rebooted, and now sda3 is automounted and no password is needed.

However, it no longer appears in my Places menu, or under Computer. Is there any way to make it appear there?

Cheers. :)

---

### Post by Morbius1 on 2009-12-28
There is a way - Bookmark it.

Open Nautilus and go to /mnt/Storage. When you're there select "Bookmarks" > "Add Bookmark".

It should show up under Places.

---

### Post by Tahakki on 2009-12-28
That has worked, but it shows up as a folder rather than as a drive.

---

### Post by Morbius1 on 2009-12-28
That's the best I've got :wink:

---

