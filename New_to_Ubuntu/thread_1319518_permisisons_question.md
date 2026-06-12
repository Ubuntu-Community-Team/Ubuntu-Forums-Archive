---
title: "permisisons question"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by patchido on 2009-11-08
well, i dont understand how permissions really work, i am kind of confused, i have a partition named Data which is just my files, i automounted it by pysm(i believe thats the name) and for some reason i cant create folders inside it, is there a way to always move as root, or what can i do?

---

### Post by ibuclaw on 2009-11-08
[LIST=1]
[*]What type of filesystem is it?
[*]How is it mounted?
[*]FsTab line?
[/LIST]

Regards
Iain

---

### Post by patchido on 2009-11-08
it is an ntfs system mounted by a program from the repositories storage device manager

---

### Post by t0p on 2009-11-08
Assuming the drive is called /media/disk:


Press Ctrl+F2, then type 

```
gksudo nautilus
```Using the file manager window that opens, go to /media

Right-click on 'disk' and select Properties

Click on the Permissions tab

If your user name does not have read and write permissions, change them so it does.

Of course, if the drive in question isn't called /media/disk, edit the commands to suit.

---

### Post by HotShotDJ on 2009-11-08
> **t0p said:**
> Assuming the drive is called /media/disk:


Press Ctrl+F2, then type 

```
gksudo nautilus
```I do not recommend this method.  You should fix the problem at its source, not perform a work-around.  Also, only removable storage (such as usb drives, cdrom, floppy drives) should be mounted in /media.  I do need to know how you envision using this "Data" partition.  Do you want it to be read/write for all users?  Just for you? Are you the only user on the machine, making that question moot?  The best solution depends on the answers to these questions.

---

### Post by patchido on 2009-11-08
it told me i cant change owner, read only file system :S

---

### Post by HotShotDJ on 2009-11-08
> **patchido said:**
> it told me i cant change owner, read only file system :SThis should be a very easy fix... but I need more info before suggesting the proper way to do it. :)

---

### Post by SuperSonic4 on 2009-11-08
chowning it to your user seems the best. I'm guessing your data partition is not removable in the sense of being a USB or eSATA device but rather an internal hard drive. In which case I'd use /mnt , put it in fstab and then chown it to your user.

Do these one at a time

```
sudo mkdir /mnt/Data
```
```
sudo nano /etc/fstab
```

Do either of the following:

**1** Add the following line to fstab (I will assume it is [COLOR="Red"]/dev/sdb1[/COLOR] but you can use ```
sudo fdisk -l
``` to find out)

```
/dev/sdb1   /mnt/Data   ntfs-3g  defaults 0 0
```


**2** Add the following line to fstab using your UUID (this is better as it's more of a solid link). Find out your UUID with ```
sudo blkid
``` - I will assume it is **[COLOR="Red"]11aa1a11-aa1a-11aa-1a11-11aaaa11aa1a[/COLOR]** but you should paste the output of the above command for the relevant drive.

```
UUID=11aa1a11-aa1a-11aa-1a11-11aaaa11aa1a  /mnt/Data  ntfs-3g  defaults 0 0
```


Now you can test mounting the drive by issuing  ```
sudo mount -a
```

If all goes well you can now chown the drive to your user ```
sudo chown -Rv [COLOR="Red"]user[/COLOR]:[COLOR="Blue"]group[/COLOR] /mnt/Data
```

et voila - ready to use and will mount on boot

---

### Post by patchido on 2009-11-08
that didnt work, and for some strange reason now the partition wont even appear in computer tab

---

### Post by HotShotDJ on 2009-11-08
> **patchido said:**
> that didnt workWhat, exactly, didn't work?  Really, we're playing a guessing game with the way that you are responding here.  SuperSonic4's method is the preferred method of accomplishing what I am again guessing is your desired goal.  If you provide us with the exact steps you performed, I'm sure we can figure out what is going wrong.  But "that didn't work" is not enough to allow us to help you.

---

### Post by patchido on 2009-11-08
im sorry, well i uninstlled the program i had that i mentioned before, and in fstab i tried to erase what shouldnt be there, after that i used the uuid name to mount it and now it is not even mountable via GUI in computer tab

---

### Post by HotShotDJ on 2009-11-08
> **patchido said:**
> im sorry, well i uninstlled the program i had that i mentioned before, and in fstab i tried to erase what shouldnt be there, after that i used the uuid name to mount it and now it is not even mountable via GUI in computer tabOk.. lets try it this way so that I can be clear about the current state of your system.  Please open a terminal (Applications -> Accessories -> Terminal) and type the following commands:```
cat /etc/fstab > fstab.txt
sudo fdisk -l > partitions.txt
```Please attach the two files that you've just created to your next post.

---

### Post by patchido on 2009-11-08
here they are

---

### Post by HotShotDJ on 2009-11-08
> **patchido said:**
> here they areExcellent.  Ok... the UUID for your "Data" partition doesn't look right to me.  But lets not worry about that.  On the last line, replace "UUID=332FA99F102D6B2A" with /dev/sda4 for now (while I agree with using UUID rather than devices, for your purposes, I think we should just stick with the device -- at least until we get it working)

Next, I'd like you to run the following commands:
```
sudo rmdir /mnt/Data
sudo mkdir /mnt/Data
```
If you get an error, please copy down the exact error you get.  But all should go well with those two commands.

After you fix /etc/fstab do the above two commands, please completely reboot your system.  Let me know if you now have read/write access to your data directory.

---

### Post by patchido on 2009-11-08
rmdir: failed to remove `/mnt/Data': Device or resource busy



i couldnt remove the directory

---

### Post by HotShotDJ on 2009-11-08
> **patchido said:**
> rmdir: failed to remove `/mnt/Data': Device or resource busy

i couldnt remove the directoryOk.  Please type "sudo umount /dev/sda4" (notice, the command is umount, not unmount!) and if no error, then try the rmdir/mkdir codes again.

---

### Post by patchido on 2009-11-08
i did unmount it successfully and then removed and created the directory but still no mounting :S

---

### Post by sisco311 on 2009-11-08
> **patchido said:**
> i did unmount it successfully and then removed and created the directory but still no mounting :S

[http://psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://psychocats.net/ubuntu/mountwindows#ntfsconfig")

---

### Post by HotShotDJ on 2009-11-08
> **sisco311 said:**
> [http://psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://psychocats.net/ubuntu/mountwindows#ntfsconfig")ARGHHH!!!  $&%*^&$   I completely forgot about that utility.  

patchido:  Undo all changes that we made to /etc/fstab, remove the directory that we created.  Now, follow the link sisco311 mentioned and follow that.

/me is feeling stupid now. :(

---

### Post by patchido on 2009-11-08
for some strange reason the partition didnt appear in there

---

### Post by sisco311 on 2009-11-08
> **patchido said:**
> for some strange reason the partition didnt appear in there

you have to remove the fstab entry of the partition before you run ntfs-config and probably unmount the partition.


please post the output of:
```
cat /etc/fstab
sudo fdisk -l
sudo blkid 
mount 
ls /media
```

---

### Post by patchido on 2009-11-08
```
pato@pato-Linux-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=6a432be5-72fe-4164-8f44-cff1a512805f / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda4 /mnt/Data ntfs-3g defaults 0 0

```
```
pato@pato-Linux-laptop:~$ sudo fdisk -l
[sudo] password for pato: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe6eb59ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2491    20007933+   7  HPFS/NTFS
/dev/sda2            2492        4981    20000925   83  Linux
/dev/sda3            4982        5242     2096482+  82  Linux swap / Solaris
/dev/sda4            5243       14593    75111907+   7  HPFS/NTFS

```
```
pato@pato-Linux-laptop:~$ sudo blkid 
/dev/sda1: UUID="86BA4A71BA4A5E35" TYPE="ntfs" 
/dev/sda2: UUID="6a432be5-72fe-4164-8f44-cff1a512805f" TYPE="ext3" 
/dev/sda3: LABEL="swap" UUID="d7a73706-36f4-47ad-ad28-8d2709517b75" TYPE="swap" 
/dev/sda4: UUID="332FA99F102D6B2A" LABEL="Data" TYPE="ntfs" 
```
```
pato@pato-Linux-laptop:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda4 on /mnt/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pato/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pato)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=pato)

``````
ls /media
cdrom  cdrom0

```

---

### Post by sisco311 on 2009-11-08
Edit fstab:
```
gksu gedit /etc/fstab
```

remove the last line(bold):
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=6a432be5-72fe-4164-8f44-cff1a512805f / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
**/dev/sda4 /mnt/Data ntfs-3g defaults 0 0**
```
and try ntfs-conf again.

or

edit fstab and replace the last line with:
```
UUID=332FA99F102D6B2A /mnt/Data ntfs defaults,dmask=002,umask=113,gid=46 0 0
```

create the mount point:
```
sudo mkdir /media/Data
```

add your user to the plugdev group:
```
sudo adduser **username** plugdev
```
replace **username** with your login name.

and mount the partition:
```
sudo mount -a
```

---

