---
title: "mnt why are you here?"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by carrarin on 2009-07-06
seriously, the os auto mounts devices in the /media folder. whats the point of haveing mnt. 


Anyways, i have three questions. with the ln command, what is the difference between a hard link and a symbolic link. I checked the man page it sucks. 

how do i turn off the auto mount?

how do i format things with fdisk?

---

### Post by rbc on 2009-07-06
I believe /mnt intended for mounting other internal hard drive partitions

1. The only thing I know about links is that hard links cannot span partitions, not true of soft/symbolic links

2. Press Alt+F2, type in gconf-editor, then navigate to Apps-->Nautilus-->Preferences, and uncheck Automount removable media. Keep in mind, though, that this prevents all removable media from automounting, including CDs and DVDs

---

### Post by carrarin on 2009-07-06
thanks!

---

### Post by Christmas on 2009-07-06
Soft links just point to a file, like a simple shortcut, while a hard link makes something like virtual files or something like that. When you modify a hard link, the original file and all other hard links are modified at the same time. I'm not sure whether this is the correct explanation though.

To turn off auto mounting, search for a tutorial on editing /etc/fstab. I've never tried fdisk.

---

### Post by cariboo on 2009-07-06
I always use /mnt to mount isos:

```
sudo mount -o loop nameofiso.iso /mnt
```

---

### Post by ugm6hr on 2009-07-06
> **carrarin said:**
> seriously, the os auto mounts devices in the /media folder. whats the point of haveing mnt. 

It is not the "OS" that mounts devices, it is nautilus (the File Manager).

Hence, mnt is necessary for the "OS" to be able to mount devices without nautilus (or other automounting software).

Remember, Ubuntu also comes as a non-GUI server.

---

### Post by egalvan on 2009-07-06
Also, **/mnt** doesn't put an icon on the desktop.

---

### Post by egalvan on 2009-07-06
Doesn't the **noauto** option in fstab turn off automount?

sorry, double-shift at the fire-house, and I'm too tired to look it up :)

---

### Post by Elfy on 2009-07-06
I mount all my internal drives in /mnt then I don't have to turn showing drives off and can lett external's and cd's show on the desktop

---

