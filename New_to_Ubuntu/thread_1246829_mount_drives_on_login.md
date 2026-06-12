---
title: "mount drives on login"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by wirate on 2009-08-22
my wubi installation mounts partitions other than the one it is installed in when I open them. I want to automatically mount my other partitions  as I login. How do i do that?

---

### Post by ibuclaw on 2009-08-22
> **waqar said:**
> my wubi installation mounts partitions other than the one it is installed in when I open them. I want to automatically mount my other partitions  as I login. How do i do that?

Have a look at this thread for reference: [http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

Can you post the output of:
```
fdisk -l
```
Then we can look into making the mount permanent.

I'm pretty sure that Windows will be on the sda1 partition, but you never know with OEM implementations.

Regards
Iain

---

### Post by louieb on 2009-08-22
file /etc/fstab controls what gets mounted where at boot. 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by wirate on 2009-08-23
this is the fdisk -l output


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1eea1eea

   Device        Boot       Start                  End                    Blocks            Id              System
/dev/sda1         *                          1         5099          40957686              7      HPFS/NTFS
/dev/sda2                            5100             18153           104856255             7      HPFS/NTFS
/dev/sda3                         18154       38913           166754700             7       HPFS/NTFS

---

### Post by powel212 on 2009-08-23
The easy way. 

No need to edit fstab.

Go to Add\Remove and install NTFS configuration tool.

Once installed launch it from System\Administration\NTFS configuration tool. Follow the steps and now your drives will be automatically mounted at startup.

Easy

Hope that helps.

Powel

---

