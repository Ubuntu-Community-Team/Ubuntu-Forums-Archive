---
title: "Confusion To mount"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Mogrix on 2009-08-12
New linux ubuntu user from long time windows User.

I'm a little confused about the concept concerning the CDROM. 

Everytime i insert a CD i have to mount the device to use the cd that i've entered?

I seem to recall a friend being able to insert his cd's and him being able to click the device from computer -- similar to windows, and loading the contents.

Everytime i put in an Audio, Game disc, or what have you, I'm told the 

"Unable to mount location"

so then i mount the cdrom with the following command

sudo mount /dev/scd0

and i recieve a message

mount: block device /dev/sr0 is write-protected mounting read-only

but next time i restart my computer i have to mount it again???

can Someone please clarify what that message means to me, and how i can get my cdrom to auto-use cd's like it does with windows?

---

### Post by CatKiller on 2009-08-12
> **Mogrix said:**
>  Everytime i insert a CD i have to mount the device to use the cd that i've entered?

No. A filesystem does have to be mounted before you can use it, but you don't have to do it manually. CDs should auto-mount, just as they do for your friend. Something is wrong with your setup.

I've not experienced this problem before, so I don't know what your problem might be. Checking that you are able to both "Access external storage devices automatically" and "Use CD-ROM drives" in the Users and Groups tool might be a good place to start, though.

---

### Post by Mogrix on 2009-08-12
Something i had forgotten to mention at the time of writing is that When i first Installed ubuntu last week i didn't have this problem. I've been trying to do some special Installation (Installing World of Warcraft) and i remember someone giving me some commands to get one of the discs to install (Wrath of the Lich King).

However i have just now discovered this problem with my CD-ROM. I'm guessing my problem is related to this, But how do i revert the process?

These were the commands that were given to me (Listed Below). Does someone know how to revert this if this indeed caused my CDROM issue i described earlier?

$ sudo mkdir /mnt/lich
$ sudo su -
# mount -t udf -o ro,unhide,uid=1000 /dev/scd0 /mnt/lich (replace /dev/scd0 with your cdrom)
# exit
$ cd /mnt/lich
$ wine Installer.exe

---

### Post by CatKiller on 2009-08-12
I'm not that familiar with permissions, or the mount command, but I don't see anything there that would survive a re-boot. ```
sudo umount /mnt/lich
``` should be enough to unmount it if it's still there.

---

### Post by zeroseven0183 on 2009-08-12
How about your settings in the** Removable Drives and Media**? Go to **System** > **Preferences**. You should see there options to mount removable drives when inserted, hot-plugged, auto-run programs on new drives and media, etc.

---

### Post by Mogrix on 2009-08-13
I issued the command to attempt and unmount Lichking. the output was 

umount: /mnt/lich: not mounted

I then went to System > Preferences > _____ But i don't have Removable Drives and Media to select from

Am i suppose to?

---

### Post by halitech on 2009-08-13
whats the output of 
```
cat /etc/fstab
```

Are you using Ubuntu, Xubuntu or Kubuntu?

---

### Post by Mogrix on 2009-08-13
I am using Ubuntu 9.04

I have for some reason the following fstab files:

fstab  
fstab.BAK 
fstab.save
fstab.save.1
fstab.save.2
fstab.save.3
fstab_bakup

The fstab file reads:

UUID=153ca5eb-bca3-40d9-9531-4243f1d8259f
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=956f85cd-87e3-4b9b-a357-9b4e054dcac7  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda5 during installation
UUID=685238d1-165c-47dd-b7df-badb8244589b  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdb1                                  /media/sdb1     ext3         defaults                    0  0

---

### Post by halitech on 2009-08-13
the .BAK and .save are backsup that have been made for some reason, only the actual fstab file is read and used

the entry for the cd looks fine and almost the same as mine.

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

you could try removing the exec and utf8 options to see if that makes any difference.

---

### Post by Mogrix on 2009-08-13
removing exec and utf8 didn't change anything upon a reboot.

If i have backups of my Fstab, perhaps i made them before i had these problems? 

How do i replace my exisiting fstab with the backups? just rename the backup and delete the existing fstab?

---

### Post by CatKiller on 2009-08-13
> **Mogrix said:**
> How do i replace my exisiting fstab with the backups? just rename the backup and delete the existing fstab?

Pretty much. You might want to rename the existing fstab too, rather than deleting it. Just in case.

FWIW, I don't have an entry for my drive in fstab at all, and automounting works as it should. You could try commenting out that line by putting a # at the start of it to see if that helps.

---

### Post by Mogrix on 2009-08-13
replacing that backup file with the existing one worked just fine... even though they both looked identical. 

???

Go figure :p

I appreciate everyone's help.

---

