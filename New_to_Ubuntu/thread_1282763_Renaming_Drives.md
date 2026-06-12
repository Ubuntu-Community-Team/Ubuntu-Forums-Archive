---
title: "Renaming Drives"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by dholcomb on 2009-10-04
I just installed a new SATA hard drive, and it shows up under computer in places as "1500 GB media". I can change the partition name with GParted, but this does not seem to have any effect on the displayed name of the drive. Nautilus will not change it, and gives me an error when I try. Any ideas?

---

### Post by renkinjutsu on 2009-10-04
try doing it with nautilus while it's unmounted

worked for me.. but you may have to create your own directory in /media .. name it whatever you like.. and then set nautilus to mount your drive to that directory.. and your drive would show with that name on nautilus

---

### Post by Mylorharbour on 2009-10-04
Hi dholcomb, welcome aboard!

I think e2label is what you're looking for.
Try, in a terminal, sudo e2label /dev/sda*? <new label>*. Just change the sda number for the one indicated in gparted and choose a label.

Tip - Don't use spaces in your labels. You can get in a hell of a mess when you try running commands in the terminal if you do.

Cheers

---

### Post by renkinjutsu on 2009-10-04
> **Mylorharbour said:**
> Hi dholcomb, welcome aboard!

I think e2label is what you're looking for.
Try, in a terminal, sudo e2label /dev/sda*? <new label>*. Just change the sda number for the one indicated in gparted and choose a label.

Tip - Don't use spaces in your labels. You can get in a hell of a mess when you try running commands in the terminal if you do.

Cheers

he's looking to change how it's displayed in Nautilus, not to the linux kernel.. i think that's what he wants

---

### Post by falconindy on 2009-10-04
It's being given that name because its being auto-mounted by FUSE and not by fstab. Find out the drive ID and give it a permanant mount point and home in /etc/fstab. If you know the dev ID (e.g. sdb, sdc, etc), you can do this (let's assume its /dev/sdb1):
```
sudo vol_id /dev/sdb1
```
Copy that UUID to the clipboard, and fire up your favorite text editor with root privileges for /etc/fstab. Make a new line like this:
```
UUID=4ceb60b7-9c0a-425a-9ef5-3526713f53df    /mnt/point   ext4    defaults    1    1
```
Obviously some things in here will differ: the UUID, where you choose to make the mount point, and the file system type (I used ext4 here).

Also, don't forget that if you need to make the mount point as root (such as in / or /mnt), you'll want to chown the mount point to yourself after its created and before you mount the drive:
```
sudo chown user:user /mnt/point
```

---

### Post by dholcomb on 2009-10-04
The directory that it is mounted in is called what I want it to be called, but it is not taking that name. I have also used e2label to change the label successfully, but again, it does not call itself by the partition label.

Finally, there is not a folder for fstab in /etc. Should I create one, or do I need to install something first maybe?

Also, for whatever reason, if I run gksudo nautilus, the drive shows up with the correct name in the sidebar.

---

### Post by falconindy on 2009-10-04
> **dholcomb said:**
> The directory that it is mounted in is called what I want it to be called, but it is not taking that name. I have also used e2label to change the label successfully, but again, it does not call itself by the partition label.

Finally, there is not a folder for fstab in /etc. Should I create one, or do I need to install something first maybe?

Also, for whatever reason, if I run gksudo nautilus, the drive shows up with the correct name in the sidebar.
/etc/fstab is a file, not a directory. I assure you its there, because without it, Ubuntu would not boot.

The name of the mount point is not the name of the drive.

---

### Post by renkinjutsu on 2009-10-04
> **dholcomb said:**
> The directory that it is mounted in is called what I want it to be called, but it is not taking that name. I have also used e2label to change the label successfully, but again, it does not call itself by the partition label.

Finally, there is not a folder for fstab in /etc. Should I create one, or do I need to install something first maybe?

Also, for whatever reason, if I run gksudo nautilus, the drive shows up with the correct name in the sidebar.

fstab is not a folder, but a text file in your /etc directory

and when you edit your fstab, instead of putting just defaults for option, you could try adding things like ```
rw,user,exec,auto
```
so you won't have to be ROOT to access the mounted device, and so nautilus (when ran by a normal user) would probably see the correct name too

---

### Post by dholcomb on 2009-10-04
I did all that, and it mounts using fstab from the file, but it still has the same name. I tried both putting in /dev/sta1 and the UUID. Both work in terms of mounting it, but neither gives it the correct name. I also tried putting in the commands instead of default, but could tell no difference.

Also, I would like to rename the original main partition. It is called "Filesystem". Is is also being loaded from fstab, but I dont know where it is getting these names from.

---

### Post by falconindy on 2009-10-04
Since you've updated your fstab, have you rebooted? Or, done the following:
```
sudo umount /dev/sta1
sudo mount -a
```

/dev/sta1 is an awfully peculiar name... would you care to post the output of `sudo fdisk -l`?

---

### Post by dholcomb on 2009-10-04
I did unmount and remount it, with no success. I typod the name, its actually sda1. There are actually 3 drives, the main one sdb (filesystem) and two others (sda and sdc) that keep getting labelled by their sizes. Here is fdisk:

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b20d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182401  1465136001   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07fcd700

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14219   114214086   83  Linux
/dev/sdb2           14220       14593     3004155    5  Extended
/dev/sdb5           14220       14593     3004123+  82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00058e6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241   83  Linux

---

### Post by falconindy on 2009-10-04
If the drive is still showing up under 'Places', then it's still being mounted by FUSE. I presume if you go into Nautilus you have an 'eject' icon next to the drive? Could you perhaps post the contents of your "/etc/fstab" and output of `df -h`?

---

### Post by dholcomb on 2009-10-04
Here is df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             108G   29G   74G  29% /
tmpfs                 502M     0  502M   0% /lib/init/rw
varrun                502M  236K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  168K  502M   1% /dev
tmpfs                 502M  124K  502M   1% /dev/shm
lrm                   502M  2.2M  500M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sr0              3.5G  3.5G     0 100% /media/cdrom0
/dev/sda1             1.4T  198M  1.3T   1% /media/drive2


And here is /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6a9030a4-1815-4365-a421-795b5af20d46 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=69eccf60-b8dc-41e6-8724-d7e3e6a6783a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=67194e6f-ecf7-4f18-8669-507756e575d8    /media/drive2    ext3    rw,user,exec,auto    0    2

---

### Post by dholcomb on 2009-10-04
Update: Apparently just unmounting and remounting the drive was not enough. After a reboot, the new drive shows up with the proper name. However, it still shows up under places, and has an eject option, so fuse might still be mounting it?

Also, does anybody know how to change the name of the partition linux is installed on to something other than filesystem?

---

### Post by falconindy on 2009-10-04
> **dholcomb said:**
> Here is df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             108G   29G   74G  29% /
tmpfs                 502M     0  502M   0% /lib/init/rw
varrun                502M  236K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  168K  502M   1% /dev
tmpfs                 502M  124K  502M   1% /dev/shm
lrm                   502M  2.2M  500M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sr0              3.5G  3.5G     0 100% /media/cdrom0
**/dev/sda1             1.4T  198M  1.3T   1% /media/drive2**


And here is /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6a9030a4-1815-4365-a421-795b5af20d46 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=69eccf60-b8dc-41e6-8724-d7e3e6a6783a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
**UUID=67194e6f-ecf7-4f18-8669-507756e575d8    /media/drive2    ext3    rw,user,exec,auto    0    2**
I'm going to assume the lines I've bolded is the drive in question. I'm no expert when it comes to mounting options in /etc/fstab, but I think I understand the options you've given and I can't think of any conflicts (although it does occur to me that I need to rewrite my own fstab). Could you perhaps try to mount the drive somewhere else? Seeing it in the /media directory makes me think its still automounting -- /media is typically used for removable drives like flash and DVDs. Make a directory /mnt/drive2 and try mounting it there.

Also, FWIW, if you don't like the idea of using defaults and want to specify individual options for drives,you'll probably want to use something like "rw,auto,exec,nodev". Having a user flag is somewhat superfluous with the auto flag, since the system (root) will mount the drive automatically on boot. The only time that would then come into play if you had to unmount/remount the drive (perhaps for a fsck) in the middle of a session.

Wikipedia has a good explanation of all the settings in [fstab](http://en.wikipedia.org/wiki/Fstab).

---

