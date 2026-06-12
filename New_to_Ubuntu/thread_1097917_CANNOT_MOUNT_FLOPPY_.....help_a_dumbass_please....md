---
title: "CANNOT MOUNT FLOPPY .....help a dumbass please..."
date: 2009-03-16
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-03-16
OK I admit it I'm a dumbass and need serious help. My floppy shows up in the hardware under Places. I can right click Rescan and here the floppy be accessed. Under Places>Computer>Floppy Drive I get a Unable to mount location.......can't mount file error. I've tried different floppy disks as well. Until someone comes to my aid it's back to the XP partition to use my floppy disk....sheeeeezz....this sucks.

Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9360d76a-ddb7-4a4a-8a92-21d35c903ad3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2d31d0c7-73ab-4b92-a354-c34d2bb6bf5c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

# Floppy Drive
/dev/fd0     /media/floppy0     auto     rw,user,noauto,exec,utf8    0  0

*****************************************************

I've done the modprobe floppy and mount /dev/fd0/media/fd0

and this stuff:

eld@House:/root$ ls /media
cdrom  cdrom0  cdrom1  floppy0
eld@House:/root$ 

Frustrated,

Ed

---

### Post by taurus on 2009-03-16
What is the error message when you try to mount it by hand from a terminal?

Applications -> Accessories -> Terminal
```
sudo mount -t vfat /dev/fd0 /media/floppy0
```

p.s.  Maybe it's time to switch to USB thumbdrives.  ;)

---

### Post by ozark_hillbilly on 2009-03-17
> **taurus said:**
> What is the error message when you try to mount it by hand from a terminal?


eld@House:~$ sudo mount -t vfat /dev/fd0 /media/floppy0
[sudo] password for eld: 
mount: special device /dev/fd0 does not exist
eld@House:~$ 



p.s.  Maybe it's time to switch to USB thumbdrives.  ;)

I use an older Sony camera that has a floppy disk drive. 
Takes good pictures, works well for me.

Ed

---

