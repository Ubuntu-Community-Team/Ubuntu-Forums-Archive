---
title: "How to auto mount drive"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by natman on 2010-10-04
Hi,
I have my hdd partitioned into three drives, one ext4, one ntfs, one fat32. In my file browser when i click on the fat32 i get asked permission for my password to mount the drive.
How do i get this to happen automatically at boot?

---

### Post by bodhi.zazen on 2010-10-04
Add or edit your entry i n/etc/fstab, add the options auto and users.

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

For details and additional options.

---

### Post by natman on 2010-10-04
There is no folder there, in the terminal it does not show any fstab inside etc.
If it makes any difference im using Kubuntu

---

### Post by Crazedpsyc on 2010-10-04
you might try adding the command 
```
gksudo mkdir /media/yourdevicename; gksudo mount -t fuseblk /dev/yourdevice /media/yourdevicename
```
to the startup command list program

---

### Post by andrewthomas on 2010-10-04
> **natman said:**
> There is no folder there, in the terminal it does not show any fstab inside etc.
If it makes any difference im using Kubuntu
the file is 

**/etc/fstab**


post the output of 

```
cat /etc/fstab
```

---

