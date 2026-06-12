---
title: "How to Fix Automount NTFS Partition Annoyance"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by TeriBash on 2010-06-17
I need some help with fixing a minor annoyance. I have Ubuntu installed as well as another OS, I recently had to reinstall the other OS and of course it changed the bootloader to only recognize windows. I went through and reinstalled grub and everything works fine, but now when loading Ubuntu it wants to automount the /dev/sda1 twice (the old install of the other OS, and the new install of the other OS) I need to know how to change this. I think I may just need to edit out a line in fstab but I want to make sure before doing anything stupid.

---

### Post by sisco311 on 2010-06-17
Hi and welcome to the forums!

Please open a terminal and post the output of:
```
sudo blkid
```
and
```
cat /etc/fstab
```

---

### Post by TeriBash on 2010-06-17
/dev/sda1: UUID="DE229D46229D2515" TYPE="ntfs" 
/dev/sda2: UUID="d53aaffe-241d-418a-a525-ef410a8d8631" TYPE="ext4" 
/dev/sda3: LABEL="STORAGE" UUID="581ED336263B12B3" TYPE="ntfs" 
/dev/sda4: LABEL="Games" UUID="336E248D0F852B76" TYPE="ntfs" 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda2 :
UUID=d53aaffe-241d-418a-a525-ef410a8d8631    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda4 :
UUID=336E248D0F852B76    /media/Games    ntfs    defaults,nls=utf8,umask=0222    00
#Entry for /dev/sda3 :
UUID=581ED336263B12B3    /media/STORAGE    ntfs    defaults,nls=utf8,umask=0222    00
#Entry for /dev/sda1 :
UUID=DE229D46229D2515    /media/Windows    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
UUID=2AF2FADDF2FAABE7    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    00
/mnt/512Mb.swap    none    swap    sw    0    0

---

### Post by sisco311 on 2010-06-17
Yep, you have to comment out/delete the penultimate line:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc nodev,noexec,nosuid 0 0
#Entry for /dev/sda2 :
UUID=d53aaffe-241d-418a-a525-ef410a8d8631 / ext4 errors=remount-ro 0 1
#Entry for /dev/sda4 :
UUID=336E248D0F852B76 /media/Games ntfs defaults,nls=utf8,umask=0222 00
#Entry for /dev/sda3 :
UUID=581ED336263B12B3 /media/STORAGE ntfs defaults,nls=utf8,umask=0222 00
#Entry for /dev/sda1 :
UUID=DE229D46229D2515 /media/Windows ntfs defaults,nls=utf8,umask=0222,nosuid,nodev 0 0
**#UUID=2AF2FADDF2FAABE7 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 00**
/mnt/512Mb.swap none swap sw 0 0
```

---

### Post by TeriBash on 2010-06-17
Thank you very much for your help. I thought that was the case but wasn't completely sure. One more quick question about this. When I go to unmount the drive in Nautilus by clicking the arrow I get this message:

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=336E248D0F852B76 from /media/Games

What would I need to do to be able to have the drive unmount by just clicking the unmount button?

---

### Post by Groodles on 2010-06-17
By having the mount points detailed in the fstab, they are mounted by root at boot.  Hence only root (or a sudo umount) can remove them.

What you "could" do is comment out all the lines which reference /media/ .  Ubuntu will still mount the other drives automatically, but they'll be mounted as your user and you'll be able to unmount them at will.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc nodev,noexec,nosuid 0 0
#Entry for /dev/sda2 :
UUID=d53aaffe-241d-418a-a525-ef410a8d8631 / ext4 errors=remount-ro 0 1
#Entry for /dev/sda4 :
**#UUID=336E248D0F852B76 /media/Games ntfs defaults,nls=utf8,umask=0222 00**
#Entry for /dev/sda3 :
**#UUID=581ED336263B12B3 /media/STORAGE ntfs defaults,nls=utf8,umask=0222 00**
#Entry for /dev/sda1 :
**#UUID=DE229D46229D2515 /media/Windows ntfs defaults,nls=utf8,umask=0222,nosuid,nodev 0 0**
**#UUID=2AF2FADDF2FAABE7 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 00**
/mnt/512Mb.swap none swap sw 0 0

```

---

