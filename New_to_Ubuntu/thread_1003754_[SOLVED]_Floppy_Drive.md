---
title: "[SOLVED] Floppy Drive"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by bj218 on 2008-12-06
When I clk on computer I no longer see my floppy drive icon. 
How do I get this back so I can use my floppy drive?

---

### Post by cmay on 2008-12-06
try
> mount fd0

---

### Post by Paqman on 2008-12-06
> **bj218 said:**
> When I clk on computer I no longer see my floppy drive icon. 
How do I get this back so I can use my floppy drive?

You might want to open up the box and check that the power and data cables to/from the floppy drive are connected properly.

---

### Post by linux_tech on 2008-12-06
```
mount /dev/fd0 
```

---

### Post by arrange on 2008-12-06
Could this help you? [https://answers.launchpad.net/ubuntu/+question/52988]("https://answers.launchpad.net/ubuntu/+question/52988")

---

### Post by bj218 on 2008-12-07
> **arrange said:**
> Could this help you? [https://answers.launchpad.net/ubuntu/+question/52988]("https://answers.launchpad.net/ubuntu/+question/52988")

This is the result of running the commands suggested.

bill@bill-desktop:~$ mount fd0 
mount: can't find fd0 in /etc/fstab or /etc/mtab 
bill@bill-desktop:~$ mount /dev/fd0     I did not get a response to this command

This command was taken from “52988”
bill@bill-desktop:~$ sudo gedit /etc/modules 
[sudo] password for bill: 
# /etc/modules: kernel modules to load at boot time. 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 

fuse 
lp 
floppy  
I added the word (floppy) and saved the above. This is rerun of this command. 

It looks like my problem has been solved!!
Now If I go to places and clk on Computer in the next window I see a new icon“UBD98” has been added and it looks just like the other drives on my system. If I rt clk this icon and select Mount I get a new icon that looks like a floppy disk.
I had a floppy with data on it in the drive when I booted up. Is it possible to change the name of the icon to floppy?

---

### Post by scorp123 on 2008-12-07
> **bj218 said:**
> mount /dev/fd0
I did not get a response to this command because it worked ;)

If there is no complaint or any error message then this means the command worked and did what you wanted it to do.

---

### Post by bj218 on 2008-12-09
> **bj218 said:**
> This is the result of running the commands suggested.

bill@bill-desktop:~$ mount fd0 
mount: can't find fd0 in /etc/fstab or /etc/mtab 
bill@bill-desktop:~$ mount /dev/fd0     I did not get a response to this command

This command was taken from “52988”
bill@bill-desktop:~$ sudo gedit /etc/modules 
[sudo] password for bill: 
# /etc/modules: kernel modules to load at boot time. 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 

fuse 
lp 
floppy  
I added the word (floppy) and saved the above. This is rerun of this command. 

It looks like my problem has been solved!!
Now If I go to places and clk on Computer in the next window I see a new icon“UBD98” has been added and it looks just like the other drives on my system. If I rt clk this icon and select Mount I get a new icon that looks like a floppy disk.
I had a floppy with data on it in the drive when I booted up. Is it possible to change the name of the icon to floppy?

Could someone tell me if I can change the "UBD98" to the word Floppy if so how do I do it?

---

### Post by linux_tech on 2008-12-10
I think you want to change the volume label.  Do fdisk -l
to verify what filesystem 1st. 

If the it is a usb floppy, depending on the filesystem you can do either e2label (ext2,3) For FAT16 and FAT32 partitions, use mtools
should work on floppy as well
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

If it is an internal floppy, you can label internal disks, but to change their mount points, use MoveMountpointHowto which uses the file called Fstab. [https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)

---

### Post by bj218 on 2008-12-10
Thanks problem solved. You'r help did it.

---

