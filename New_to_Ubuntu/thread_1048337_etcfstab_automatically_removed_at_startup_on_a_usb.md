---
title: "/etc/fstab automatically removed at startup on a usb flash drive"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Ben63 on 2009-01-23
I got a persistent ubuntu live set up on a usb flash drive, but I run out of space on it. I wanted to move a part of the files on my hard drive, but the drives are not automatically mounted, and when I change the file /etc/fstab, it is automatically reset when I reboot :
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
I looked around on the internet but couldn't find any information about this.
Anybody knows about this?

---

### Post by cmnorton on 2009-01-24
Can you mount the hard drives manually at the command line and transfer non-OS files to the hard-drive?

---

### Post by Ben63 on 2009-01-24
Thanks for the answer.
The hard drive works perfectly, I can mount it, add/remove/modify files,etc.
And when I modify the file /etc/fstab to declare my hard drive and the mounting point, everything works perfectly, until I reboot. If I reboot, the file /etc/fstab is overwritten automatically to "it's default value" (the 2 lines above)
So this is not really a problem once I have a shell/terminal, as I can modify the fstab file back to the good values and mount everything.
But I would like to move most of the files to the hard drive, hence some files necessary for starting ubuntu. That's why I am looking for a way to mount my hard drive Before the need to access those files.
Also I found the fact that the file /etc/fstab is rewritten surprising!

---

### Post by cmnorton on 2009-01-25
Which /etc/fstab are you modifying? I would assume it's the one on the USB drive. 

Why /etc/fstab is re-setting is a mystery to me, but one that would be worth searching, which I will. I am wondering if you won't have to have a root shell script run issuing the mount command for you. 

Hopefully, one of the wiser Ubuntu elders will weigh in on this, too.

---

### Post by Ben63 on 2009-01-26
yes the file /etc/fstab that I am modifying is the one on the usb drive, actually all my files are on the usb drive for now.
Notice that as it is a Ubuntu live installed on this usb key, I have a partition fat32 (named ubuntu8) where I guess the original files of the live CD have been copied, and an ext2 partition (named casper-rw) that I guess gather be the results of the persistence.
The partition fat32 ubuntu8 has a folder named casper, and the ext2 partition "mounts" this folder as /rofs (read only). The content of this folder looks like a normal root filesystem. It has a /etc/fstab, but this one is empty (one comment line : # UNCONFIGURED FSTAB FOR BASE SYSTEM)

As for the root script, is there a way to make it launch before a lot initializations of ubuntu, so that I could move most of the files to the hard drive?

---

### Post by cmnorton on 2009-01-26
The script goes into  /etc/init.d/rc.local. I don't know if you can make it run before other things.

As to /etc/fstab being reset, do you see a reset message? This almost sounds like the write to /etc/fstab is not being flushed to the drive.

---

### Post by Ben63 on 2009-01-26
Thanks for pointing me to the file /etc/init.d/rc.local. I looked into it and as far as I understand the file /etc/init.d/rc.local is loaded just after the kernel.
The kernel uses the folder /.usr/lib, so I could not move this one, but I did move /usr/share that is also pretty big (1.3 GB).

Nothing on any log about the file been reset. Yeah it looks like this file can not be saved.
We can look at it more if you are interested, otherwise my problem is solved with the use of rc.local and copying pasting the fstab file from a personal backup file.

Thanks

---

