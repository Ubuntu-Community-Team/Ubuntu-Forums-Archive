---
title: "Mounted hard drive does not appear under 'Places' or on Desktop"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by frustratednerd on 2010-08-14
Hi there. I currently have a mounted slave hard drive that, for some reason, is NOT appearing under 'Places' or on the Desktop. Strangely, though, when I go to save a file it appears on the side pane as "300 GB Filesystem".

Here is my fstab:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=0f0c6281-875e-47a8-afc5-2b467c660839  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=048aa2fd-25b7-4f5a-b36c-d442e58354f0  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/sdb1     ext4  defaults                  0  0  
And here is my fdisk -l:

> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001a722

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9325    74895360   83  Linux
/dev/sda2            9325        9726     3226625    5  Extended
/dev/sda5            9325        9726     3226624   82  Linux swap / Solaris

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00028316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux
sdb1 is the mounted slave hard drive that I'm talking about. Hope someone can help. Thanks!

---

### Post by cj13579 on 2010-08-14
I had this before under Karmic. Luckily for me I just had some movies and songs on there so backed it up to an external then re-formatted and Labelled the drive with GParted.

If you have enough space to do that it worked for me.

---

### Post by Morbius1 on 2010-08-14
It would appear that this line in fstab is being ignored but it looks fine to me:
>  /dev/sdb1                                  /media/sdb1     ext4  defaults                  0  0                        From a terminal run the following command and post any errors:
```
sudo mount -a
```You might want to run the following command just to make sure that it's really ext4 and not something else:
```
sudo blkid -c /dev/null
```

---

### Post by dream_w on 2010-08-14
I don't understand very well the problem. Did you mount the drive? Can you see its contents on a terminal by typing ls?

What is the output of 
```
cat /etc/mtab
```

---

### Post by locoHost on 2010-08-14
Ok, what's the solution here? I'm having same prob. I can see the drive is mounted in term, but it doesn't show up in nautilus.

---

### Post by frustratednerd on 2010-08-14
**Morbius1**:
sudo mount -a did not give me any errors.
blkid confirms that the hard drive in question is indeed ext4.

**dream_w**:
The problem I'm having is that one of my hard drives is not appearing in Thunar in the side-pane, on the Desktop, or under 'Places' at the top. However, one odd thing is that it does appear in the side-pane when I'm trying to save a file or browsing for a file (like when trying to upload an image onto an image hosting website).
Yes, the drive is mounted, and yes, I'm able to see its contents with ls.

Here is the output of cat /etc/mtab, as you requested.
> /dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sdb1 /media/sdb1 ext4 rw 0 0


---

### Post by locoHost on 2010-08-14
My solution (found it here somewhere) was that my drive was mounted in /mnt rather than /media. Moved it to /media and also added auto to the options in fstab. That did the trick!

---

### Post by Morbius1 on 2010-08-14
Take a look at this and see if it is applicable to your situation:
[http://ubuntuforums.org/showthread.php?t=1471487](http://ubuntuforums.org/showthread.php?t=1471487)

---

### Post by frustratednerd on 2010-08-14
**Morbius1**:
I've looked through the thread and can say that the situation is similar to mine. None of the proposed solutions in the thread worked, though.

EDIT: Okay, I installed GNOME on Xubuntu, and oddly enough, the slave hard drive does indeed appear under 'Places' and on the Desktop. It also appears in Nautilus (it did not appear in Thunar). So perhaps it's just Xfce that's causing it not to show up?

---

### Post by 4Orbs on 2010-08-14
If the drive is an external hdd and plugged into a usb port: To get it to show up on Xubuntu desktop, go to the xfce4 settings manager... click on "Desktop" then click the "Icons" tab and make sure you have a checkmark in the "Removable Media" selected. If you want it to show up in the "Places" menu you only need to bookmark the drive by opening Thunar>> filesystem>> media and right click on sdb1 and select "Send to" the sidepane.

---

