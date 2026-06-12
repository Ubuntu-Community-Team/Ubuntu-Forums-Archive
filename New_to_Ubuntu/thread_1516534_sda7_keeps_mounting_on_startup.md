---
title: "sda7 keeps mounting on startup?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by walkerchuckwalker on 2010-06-23
I have a dell computer with windows vista and ubuntu. I recently downloaded Storage Device Manager to try to mount a partition. But I accidentally mounted the wrong one (sda7). I think this was the partition for the Dell Media Direct application which had its own special partition. And now every time I startup sda7 is mounted on the desktop just like when you click on unmounted drives, they show an icon on the desktop. Please help remove the remounting of this drive.

---

### Post by hansdown on 2010-06-23
Hi walkerchuckwalker.

If you right click the icon, what options does it give you?

---

### Post by Ozymandias_117 on 2010-06-23
Post the output of ```
cat /etc/fstab
```

---

### Post by oOarthurOo on 2010-06-23
Uninstall storage device manager. Mount drives properly using fstab.

---

### Post by walkerchuckwalker on 2010-06-25
This is the return:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda6 during installation
UUID=ffa4b7c3-07ee-424f-8062-a10edb145558  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda7 during installation
UUID=4b1a1c8a-3961-435c-b9d1-8c8b4eb3e099  none         swap  sw                   0  0  
/dev/sda7                                  /media/sda7  vfat  defaults             0  0

---

### Post by Ozymandias_117 on 2010-07-07
Sorry I didn't reply before :redface: just remove this like from your fstab: ```
/dev/sda7 /media/sda7 vfat defaults 0 0
``` and save. That will stop it from mounting on boot.

---

### Post by bodhi.zazen on 2010-07-07
> **Ozymandias_117 said:**
> Sorry I didn't reply before :redface: just remove this like from your fstab: ```
/dev/sda7 /media/sda7 vfat defaults 0 0
``` and save. That will stop it from mounting on boot.

I would suggest you change the options. Rather then defaults use "noauto,users"

See also :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

