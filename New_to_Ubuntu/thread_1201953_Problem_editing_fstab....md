---
title: "Problem editing fstab..."
date: 2009-07-01
forum: New to Ubuntu
---

### Post by AndrewS on 2009-07-01
Hi

I have a PC with 9.04, 8.04, 7.10 and XP installed.  I seem to have corrupted the /etc/fstab file in the 9.04 partition (the PC won't boot into that OS, but will into the others).

I can mount the 9.04 partition from 8.10 and I can see te differences between fstab and fstab.BAK (which I assume the system generated when I modified the file?)  But I can't figure how to edit the file - I get errors saying I don't have the necessary permissions.

If it helps, 9.04 is installed on /sda9, and in gparted I assigned the label Ubuntu 9.04 to that partition.  If I "ls" the contents of the /media directory in the 8.10 partition, I get (apart from the cdrom entries) Ubuntu 9.04.

Thanks in advance for your help.

Andrew

---

### Post by Michael.Godawski on 2009-07-01
hi,

to edit the fstab file you need sudo rights so:

```
gksudo gedit /etc/fstab
```

But before you edit it can you please post the content of it so we might have a look?

```
cat /etc/fstab
```

---

### Post by AndrewS on 2009-07-01
Thanks for that.  The first problem is that I can't access any files in the 9.04 partition when in a terminal.  I am told that Ubuntu 9.04 is not a directory (or something like that).  Trying to connect to /dev/sda9 doesn't work either.

The offending fstab file is as follows:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda9 during installation
UUID=15e9702b-8622-4f26-83ce-637d0060cd28  /               ext3         errors=remount-ro,users     0  1  
# swap was on /dev/sda10 during installation
UUID=530477ff-f9fc-44d5-8589-e22c4286cfac  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda2                                  /media/sda2     vfat         users                       0  0  
/dev/sda5                                  /media/sda5     ext3         errors=remount-ro,users     0  0  
/dev/sda6                                  /media/sda6     swap         noauto,sw                   0  0  
/dev/sda7                                  /media/sda7     ext3         errors=remount-ro,users     0  0  
/dev/sda8                                  /media/sda8     swap         defaults                    0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,ro,umask=000  0  0  

The differences from the fstab.BAK file are the entries for user.

Thanks

Andrew

---

### Post by rgroene on 2009-07-01
I don't know anything about editing fstab, but have you tried mounting the partition in Nautilus or whatever and then using whatever address comes up in Nautilus under location in the terminal? For instance, for me to access one of my other partitions, it is /media/disk.

---

### Post by AndrewS on 2009-07-02
Fixed!  I booted with a gparted disk, removed the label from the 9.04 partition and was then able to access that partition from the 8.04 partition (where it was now known simply as /media/disk).  I guess I shouldn't use labels with spaces?

Thanks again

Andrew

---

