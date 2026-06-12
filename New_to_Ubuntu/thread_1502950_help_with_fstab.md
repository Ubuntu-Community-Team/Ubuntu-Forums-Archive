---
title: "help with fstab"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by insanity99 on 2010-06-06
i want to make it so my two NTFS drives are mounted on startup, so i dont have to enter my password the first time i use it after startup. im not sure what i want to add to fstab,

here is my fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7eb0067a-0232-4aed-8782-16da70eed205 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=2d523f65-9d97-4066-a67a-e2b3b7c76322 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=bc314585-e75d-4f47-8fe9-4c03b92cdf1a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

thanks.

---

### Post by baddnady23 on 2010-06-06
> UUID=2d523f65-9d97-4066-a67a-e2b3b7c76322 /home ext4 defaults 0 2

If I am not mistaken, this would be your home partition and 

> UUID=7eb0067a-0232-4aed-8782-16da70eed205 / ext4 errors=remount-ro 0 1

this would be your / partition.

Try posting the output of:

```
sudo fdisk -l
```

---

### Post by Paqman on 2010-06-06
> **insanity99 said:**
> im not sure what i want to add to fstab

You don't really want to be manually editing important system files if you don't know what you're doing.

Install [ntfs-config](apt:ntfs-config) and use that, it'll sort you out in no time.

---

### Post by Morbius1 on 2010-06-06
I add lines in fstab directly to mount these partitions but I did install ntfs-config once since it's mentioned a lot in this forum.

The first time I ran it it asked me if I want to enable write support for internal and external drives. Is ntfs-config not aware that write support for NTFS is enabled by default in ubuntu and has been since like Gutsy?

And what exactly happens when you click to enable write support? Too many unknowns for my taste so I uninstalled it. :wink:

---

### Post by baddnady23 on 2010-06-06
As far as the windows goes, using ntfs-config is real easy.  Once you set your mount point and get to the option to select write support, just click on enable write support for internal or external drive, depending on which you have.  It will allow you to modify and save files to the ntfs partition, which is what I am assuming your trying to accomplish. :)

---

### Post by insanity99 on 2010-06-06
thanks guys NTFS worked.

---

