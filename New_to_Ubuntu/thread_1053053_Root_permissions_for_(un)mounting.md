---
title: "Root permissions for (un)mounting"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by NuttyMonk on 2009-01-28
Hi all,

i've only been using Ubuntu for a couple of days and have never used linux before.

I have 2 questions.

Is it possible to set up Ubuntu to automatically mount my hard disks at startup and place icons on the desktop?

Also, i inserted a CD earlier and it was mounted by root and an icon was placed on the desktop.  Now it won't let me eject the CD or unmount the drive because it says i don't have the permission to do that, only root does.  I tried changing the default usergroup for my user profile to root but that didn't help.  I've had a few problems like this before where it won't let me do something because i am not root.  Can anyone offer any advice on how to get round these probs?

Cheers

NM

---

### Post by ptn107 on 2009-01-28
The devices mounted at startup are listed in a file called /etc/fstab.  It's best you read up on this file[1,2] before you start changing stuff, and make a backup while your at it.  As for the CD you should just be able to press the button on your cd tray to eject it.  The manual way to do it would be to open up a terminal (Applications -> Accessories -> Terminal) and type the following:
```
sudo umount /media/cdrom
```
You should then be able to open your cd tray normally.

1. [_http://en.wikipedia.org/wiki/Fstab_]("http://en.wikipedia.org/wiki/Fstab")
2. [_http://www.tuxfiles.org/linuxhelp/fstab.html_]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by northern lights on 2009-01-28
You should be able to right-click the folder icon of */media/cdrom* and choose either "Eject" or "Unmount".

Further, external harddrives should be mounted automatically upon connection and be fully accessible as a regular user, unless their formatted as *nix filesystems and permissions have been set otherwise.

Internal devices settings are to be found in */etc/fstab*. Post the output of ```
sudo fdisk -l
```and```
cat /etc/fstab
```and further describe how you'd want it to be set up.

---

### Post by NuttyMonk on 2009-01-28
ptn107,

The disk wouldn't eject when i hit the button, an error message would come up in Ubuntu saying i didn't have permission  :-)  It was unmounted though when i used that code you gave me in the terminal.  Cheers

northern lights,

it wouldn't unmount or eject from Ubuntu, or when i pushed the button on the cd drive itself.  It always said i didn't have root permissions.


this is the output of "sudo fdisk -l"

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94469446

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94939493

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b2244ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36483   293049666    7  HPFS/NTFS

and this is the output of "cat /etc/fstab"

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3f9891b4-22f9-4e78-b813-d5d0c6df51cd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5c50582a-5750-448d-857e-4dfc01a8e929 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I have two other hard disks and a cd/dvd drive.  I'd like to have them mounted at startup and icons on the desktop.

From reading the info on "sudo" in the terminal, i can see that it allows a user to do something as if they were the superuser (root?).  Can't i set up my user profile to be like that all the time, and not only when i use sudo in the terminal?

Thanks for your help guys.  Getting to grips with linux is proving to be quite involved.

Cheers

NM

---

### Post by ptn107 on 2009-01-28
Can you post the output of:
```
ls -l /dev/disk/by-uuid/
```

---

### Post by NuttyMonk on 2009-01-28
total 0
lrwxrwxrwx 1 root root 10 2009-01-28 13:50 3f9891b4-22f9-4e78-b813-d5d0c6df51cd -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-01-28 13:50 5c50582a-5750-448d-857e-4dfc01a8e929 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-01-28 13:50 B2FC8F13FC8ED151 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2009-01-28 13:50 C8CCCC7BCCCC64F2 -> ../../sdb1

---

### Post by NuttyMonk on 2009-01-28
/dev/sdb1	/media/Art	fuseblk	rw,user,auto 0 0
/dev/sdc1	/media/Music	fuseblk	rw,user,auto 0 0

by checking the output of "ls -l /dev/disk/by-uuid/" against the codes shown on the properties of the disks, i have been able to identify the 2 hard disks.  Would the above code look suitable to you for mounting at startup?  The mounted disks have fuseblk as the filesystem, is that ok to use in the fstab file?

How about this for the CD drive?

/dev/scd0       /media/CDDVD   udf,iso9660 ro,user,auto,exec,utf8 0 0

I'm not sure what effect the exec has though?  Does that look ok to you?

Cheers

NM

---

### Post by NuttyMonk on 2009-01-28
p.s. or would auto be better for the filesystem type for the cd drive?

---

### Post by ptn107 on 2009-01-28
Ok you can permanently add your other two drives as follows (I am going to assume the order won't matter to you, so sdb1 is going to be the 120gb drive and sdc1 is the 300gb).  Carefully execute these commands one at a time in a terminal (or copy paste, it may ask for your password once because we're using 'sudo'):

1. Create local folders for the new drives to be mounted:
```
sudo mkdir /media/sdb1 /media/sdc1
```
2. Change the permissions on the folders you just created so you can read/write to them:
```
sudo chown $USER.$USER /media/sdb1 /media/sdc1
```
3. Back up your original fstab file in case things go south:
```
sudo cp /etc/fstab /etc/fstab.backup
```
4. Edit /etc/fstab:
```
sudo gedit /etc/fstab &
```
5. Add the following lines to the bottom of your /etc/fstab file:
```
# /dev/sdb1
UUID=C8CCCC7BCCCC64F2 /media/sdb1 fuseblk rw,user,auto 0 1
# /dev/sdc1
UUID=B2FC8F13FC8ED151 /media/sdc1 fuseblk rw,user,auto 0 1
```
So your entire /etc/fstab file will look like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=3f9891b4-22f9-4e78-b813-d5d0c6df51cd / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=5c50582a-5750-448d-857e-4dfc01a8e929 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sdb1
UUID=C8CCCC7BCCCC64F2 /media/sdb1 fuseblk rw,user,auto 0 1
# /dev/sdc1
UUID=B2FC8F13FC8ED151 /media/sdc1 fuseblk rw,user,auto 0 1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

All you should need to do now is restart the computer.
Nothing should go wrong, but if it does you can restore your original /etc/fstab file by typing the following in a terminal:
```
sudo cp /etc/fstab.backup /etc/fstab
```

Let me know of your progress.

---

### Post by ptn107 on 2009-01-28
Oh, well given your previous post you can change your /etc/fstab to this instead (sorry thought they were ntfs drives at first, my mistake):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=3f9891b4-22f9-4e78-b813-d5d0c6df51cd / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=5c50582a-5750-448d-857e-4dfc01a8e929 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sdb1
UUID=C8CCCC7BCCCC64F2 /media/sdb1 fuseblk rw,user,auto 0 1
# /dev/sdc1
UUID=B2FC8F13FC8ED151 /media/sdc1 fuseblk rw,user,auto 0 1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

The last line is for your cdrom.

**Corrected previous post as well.

---

### Post by NuttyMonk on 2009-01-29
Hi ptn107,

no luck with that code.

I've tried lots of different variations but the only way i can get to the drives is if i don't put any code for them into the fstab file.  When i click them in that situation, Ubuntu mounts them for me.

I've also tried lots of different variations but nothing seems to work.

:-(

One thing i've just noticed in your last post, is that they ARE ntfs drives (formatted in Win XP).

Does that make a difference?

---

### Post by NuttyMonk on 2009-01-29
hi,

i just realised i hadn't created the two folders you mentioned in your earlier post and changed the permission for them.  I've done that now but since i did that i now get an error saying "there is an invalid mount option when trying to mount the volume" and the volumes don't mount automatically at start up.

Any idea what that could be?

Getting there, slowly but surely  :)

---

### Post by egalvan on 2009-01-29
Do you have "ntfs-config" installed?

this will ease the situation.

of course, you will miss the learning experience of mount, fstab, etc. :)

Your call..

---

### Post by NuttyMonk on 2009-01-29
i do now.  i'll check it out in a minute and get back to you if i have any probs.

---

### Post by egalvan on 2009-01-29
One more thing,
I make sure that any NTFS drive has a drive label.
(Actually, ALL my drives/partitions have labels.)

Removable drives benefit greatly from labels.

---

### Post by NuttyMonk on 2009-01-29
i gave the drives labels when they were formatted.  "Music" and "Art".

---

### Post by NuttyMonk on 2009-01-29
Hi,

all that happens when i open up the ntfs config tool is that it gives me two radio buttons for enabling write support for external and internal htfs file systems.  The one for internal is unselectable, even if the disk is mounted or not.

Is that all it's meant to do?

---

