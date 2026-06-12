---
title: "Help with Playing CD's"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by lnknprkht on 2011-05-30
I have recently Installed Ubuntu 11.04 on a computer and read to type in cat /etc/fstab to see where my CD drive was pointed for CD's to play and this is what came up (also there is no way for me to access the internet on the computer that is running Ubuntu, for it has no wireless card or ethernet/phone jack port):

#/etc/fstab: static file system information.
#
#Use 'blkid -o value -s UUID' to print the universally unique identifier
#for a blank device; this may be used with UUID= as a more robust way to name 
#devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>    <type> <options>        <dump> <pass>
proc                   /proc                 proc       nodev,noexe,nosuid 0           0
# / was on /dev/sda during installation
UUID=0d2c39f6-a17e-49f4-8b51-8e57ebc0494b /                ext4       errors=remount
-ro 0              1           
#swap was on /dev/sda5 during installation
UUID=5ade3bf5-1f79-4a31-84c2-03124d79681 none            swap      sw
    0             0

any help understanding this would be greatly appreciated.

---

### Post by AlphaLexman on 2011-05-30
From a terminal,
```
sudo echo "/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
" >> /etc/fstab
```
And enter your password when prompted. 

You may have to logout and login for the changes to take place, possibly even reboot.

---

### Post by oldos2er on 2011-05-30
You need to install ubuntu-restricted-extras to play audio CDs, to install packages without an internet connection, see [http://keryxproject.org/](http://keryxproject.org/)

---

