---
title: "How to view/restore files in Trash on partition that mount on /opt"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Victorq10 on 2009-09-13
I have partition and .Trash folder in the root of partition.

My partition is mounted to /opt

Trash folder is /opt/.Trash

When I delete files/folders in /opt they placed in /opt/.Trash hierarchy

In Nautilus Trash I cannot view files that was been deleted in /opt.

I can only browse by directory hierarchy that was created in /opt/.Trash/1000/.... and view deleted files.

Is there possible to view in my Trash (Nautilus) folder deleted files from all partitions?

my fstab is:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sda2 during installation
UUID=965977ea-b29f-4fa0-8de2-497e4261df42  /              ext3         relatime,errors=remount-ro  0  1  
# /home was on /dev/sda7 during installation
UUID=268bfec2-85e0-4eb2-bae4-04498daf2e01  /home          ext3         relatime                    0  2  
# swap was on /dev/sda6 during installation
UUID=a0961a63-ef8e-4abd-8ba5-7cfeff03d41c  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda7                                  /opt           ext3         relatime                    0  0

---

### Post by mapes12 on 2009-09-13
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Malta paul on 2009-09-13
Each partition has its own trash folder, and can be access using root privileges. Alt+F3 'gksudo nautilus' go to your partition and you have access. Please be careful now as you are in permanent root.:D

---

### Post by Victorq10 on 2009-09-13
> **Malta paul said:**
> Each partition has its own trash folder, and can be access using root privileges. Alt+F3 'gksudo nautilus' go to your partition and you have access. Please be careful now as you are in permanent root.:D

press Alt+F2. Run Nautilus with root privileges. but when click on Trash icon in Places get Error message:
  The folder content can not be displayed.
  Sorry, could not display all the contents of "trash":Operation not supported.


What does it mean?

---

### Post by Victorq10 on 2009-09-13
I found some discussion
[http://ubuntuforums.org/archive/index.php/t-328721.html](http://ubuntuforums.org/archive/index.php/t-328721.html)
but they had same querstion.
Why all files cannot be found by Trash-icon?

---

