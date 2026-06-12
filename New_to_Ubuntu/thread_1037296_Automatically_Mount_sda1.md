---
title: "Automatically Mount sda1"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by neoMAX on 2009-01-11
I can't seem to figure out how to automatically mount my 320gb sata drive when ubuntu boots. It mounted fine in Windows, actually didn't have to mess with it, and when I boot ubuntu, I always have to go click on it in the Places menu once, then it will pop up on the desktop.

Any ideas? :\

---

### Post by drs305 on 2009-01-11
You didn't say what kind of formatting it has. However, since you mentioned windows I'll guess it is NTFS. If so, install and run ntfs-config. Whatever mountpoint you type in will be created in /media.

```

sudo apt-get update
sudo apt-get install ntfs-config
sudo ntfs-config

```
After installation, you can also find the app in Applications, System Tools, NTFS Configuration Tool.

Enter the mountpoint and check to enable write support. A mountpoint will be created and an entry will automatically be added to fstab to mount the device during boot. Again, this is for ntfs partitions.

---

