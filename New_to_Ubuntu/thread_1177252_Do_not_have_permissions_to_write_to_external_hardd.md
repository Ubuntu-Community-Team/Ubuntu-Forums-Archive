---
title: "Do not have permissions to write to external harddrive"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by simon303 on 2009-06-03
Hi,
I have just got a new external harddrive and formatted it to ext3 using gparted.
Now whenever I plug it in it is sometimes mounted, and when it is I don't have permissions to make folders or anything.
Does anyone know how to resolve this?
Thanks
Simon

---

### Post by simon303 on 2009-06-03
Using [http://ubuntuforums.org/showthread.php?t=201068](http://ubuntuforums.org/showthread.php?t=201068)
I have managed to make it so when it is mounted I have full read/write permissions, but when I plug it in a message pops up announcing "You are not privileged to mount the volume '1TB_backup'."
I have to mount it from the command line

Here is fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8537236e-bf88-42a3-8705-aa35fd669a62 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=425354af-b492-4236-8691-8ba6f94266bd /home           ext3    relatime        0       2
# /dev/sda3
UUID=d310d8cc-6bf5-4cc9-b895-c31bb0770e35 none            swap    sw              0       0
/dev/sda2	/mnt/windows	ntfs-3g		0	0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//hudson.dur.ac.uk/***	/mnt/jdrive	cifs	 username=***,domain=***,iocharset=utf8,uid=simon,file_mode=0700,dir_mode=0700,noauto	0	0
/dev/sdc1	/media/1TB_backup	ext3	umask=000	0	0

```

The drive in question is the last entry

---

### Post by theDaveTheRave on 2009-06-03
Simon

it sounds like you have a user permissions error for accessing extra drives.

Go into the <system | admin | users and groups > menu

Select your user name, and then select to view the properties with the button on the right hand side.

under the <User Privileges> tab one of the entries should be "access external storage devices automatically", if this isn't selected you will need to unlock the control panel (with your admin password - which should be the same as your general password), and then when you select your user name again you will be able to select this particular option.

There are other ways of doing this is this isn't what the problem is. There is a control script for automounting stuff (I'm not sure where it is though, I think it is part of the mount or fstab system) and it can be told to mount the external HDD with specified permission.

It may be of course that this particular HDD was accidentally locked when you used gparted to only allow access to root.

If this is the case you can start a file manager (eg nautilus) from a terminal
```
sudo nautilus
``` or whichever file manager you are using (eg thunar).

You will be asked for your admin password (as you have started nautilus with sudo (Super User Do). The just select the external HDD and change it's permissions.

does this help you out??

David
________edit_________

you beat me to it mate!

I have never found that my external disks "mount automatically" untill I try to access them, even then sometimes they don't work correctly.

Have you tried a reboot, as I guess you have been playing with your system (ie fstab).

David

---

### Post by simon303 on 2009-06-04
Thanks for the help.
I have removed the entry in fstab, removed /media/1TB_backup and rebooted
Not sure why, but I now seem to have full read/write access, it even mounts automatically.
I looked at the user permissions and I have always had the permission to "access external storage devices automatically"
As I said, not sure what I did that fixed it, but thanks for the help.
Simon

Edit: can't seem to mark this as solved

---

