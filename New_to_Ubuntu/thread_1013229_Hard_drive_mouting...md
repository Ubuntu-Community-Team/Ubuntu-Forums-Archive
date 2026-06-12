---
title: "Hard drive mouting.."
date: 2008-12-16
forum: New to Ubuntu
---

### Post by beaulanger on 2008-12-16
Most distros I have tried as live boot disks have the disk menus or icons available that can be easily clicked to mount and unmount. I have XP on a seperate internal hard drive and will be installing Ubuntu on another.
I installed and liked Open SUES but it didn't have a mounter built in and, even through much appreciated forum support, never was able to get my XP drive mounted through their Yast or terminal console.

Thanks.
Beau

---

### Post by taurus on 2008-12-16
If you want to mount your windows partition, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by beaulanger on 2008-12-16
> **taurus said:**
> If you want to mount your windows partition, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

Thanks. That easy huh? I'll install the 32bit on my AMD64 and give it a whirl. 
Beau

---

### Post by BGFG on 2008-12-16
You should go 64bit. Faster and smooth.

For easy GUI configuration of mounting check here:

[http://ubuntuforums.org/showthread.php?t=985765](http://ubuntuforums.org/showthread.php?t=985765)

---

### Post by beaulanger on 2008-12-16
> **BGFG said:**
> You should go 64bit. Faster and smooth.

For easy GUI configuration of mounting check here:

[http://ubuntuforums.org/showthread.php?t=985765](http://ubuntuforums.org/showthread.php?t=985765)

Appreciate that. Thanks. Been reading pros and cons on 64bit on a 64bit system. Something about Flash, etc. getting to work plus some 32bit software. I'll give it a try though.

---

