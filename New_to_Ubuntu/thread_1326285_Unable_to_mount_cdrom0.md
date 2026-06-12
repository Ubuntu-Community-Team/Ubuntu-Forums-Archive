---
title: "Unable to mount cdrom0"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by dm6257 on 2009-11-14
When I select the cdrom0 icon on my HP Pavilion ZX5000 running 9.10  I receive the following message:

mount: special device /dev/scd0 does not exist

I used the cdrom to install 9.10 and it worked on 7.10 and 8.04.

Suggestions?

---

### Post by bumanie on 2009-11-14
You could go to Administration --> Users and Groups and click on your user name and then go to Properties and check that the cdrom check box has a tick in it under the user privileges tab. If not, unlock the user settings at the unlock button via your password and check the box next to cdrom. The problem is quite possibly a permissions issue. If the cdrom is owned by root, you may have to modify ownership of the device. If that doesn't help, please post the output of > cat /etc/fstab

---

### Post by dm6257 on 2009-11-14
The CD ROM Drives box is checked in the Users and Groups administration window.  Below is the content of fstab as suggested.

Thanks,
Dale 

dale@dale-HP:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f55f0080-098f-4e66-b7fd-a24be3b27225 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3970d0b2-dd56-4e5c-97e3-435042e1e817 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by oldsoundguy on 2009-11-14
Hate to ask an obvious question, but is there a disk in the drive?  My drives will only mount when I insert a disk into them.
(exception .. floppy drive on Mythbuntu PVR mounts on boot! ... no clue as to why!!  Bios??)

---

### Post by sisco311 on 2009-11-14
run:
```
sudo lshw -C disk
```
in a terminal.

if your cdrom is detected, the command should list the logical names:
```
  *-cdrom                 
       description: DVD-RAM writer
       product: DRW-1608P3S
       vendor: ASUS
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       [B]logical name: /dev/cdrom
       logical name: /dev/cdrom0
       logical name: /dev/cdrw
       logical name: /dev/cdrw0
       logical name: /dev/dvd
       logical name: /dev/dvd0
       logical name: /dev/dvdrw
       logical name: /dev/dvdrw0
       logical name: /dev/scd0
       logical name: /dev/sr0[/B]
       version: 1.19
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open

```

replace /dev/scd0 in fsatb with one of the names listed by lshw.

---

### Post by dm6257 on 2009-11-14
Thanks for the suggestions.  I think it needed a disk in the drive.  Seems to work now.

---

### Post by jomacintosh on 2009-11-14
Hey.  I'm having the same issue...I dont' want to hijack the original post, but I'm eager to see what the solution will be.

---

