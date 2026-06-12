---
title: "no fstab"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by bobanshirl on 2010-01-01
I have recently discovered that if I wished to  add/edit anything in etc/fstab well I wont be able to,as I do not have the fstab entry in etc.I dont know what etc /fstab is for and I think if I had it I would leave well alone.I installed Ubuntu with wubi if that helps,but if anyone knows how to correct this error I would appreciate it.Many thanks.Bob

---

### Post by cariboo on 2010-01-01
Etc is a directory where most of the systems configuration files are located. You can take a tour of the file system by opening up Nautilus (Places-->Home Folder, and then selecting **File System** from the left hand pane.

To edit fstab. Press Alt-F2 and type:

```
gksudo gedit /etc/fstab
```

THe above command will open /etc/fstab as root, and allow you to edit the file.

---

### Post by phillw on 2010-01-01
Hi,

wubi is a virtualistion of ubuntu, within windows. If you like ubuntu & want to explore it more thoroughly, then I'd recommend installing ubuntu as a dual boot system. You only need 10GB of spare hard disk space for a basic installation. People do run Wubi quite happily long-term, just be aware that updates can drop you to the grub prompt, which is kinda scary for newcomers. You may want to make a note of this thread for future reference.

[http://www.uluga.ubuntuforums.org/showthread.php?t=1314064&page=7](http://www.uluga.ubuntuforums.org/showthread.php?t=1314064&page=7)

It's posting #62  that you probably need sooner or later & it's best to be aware of it before it happens !!

Regards,

Phill.

---

