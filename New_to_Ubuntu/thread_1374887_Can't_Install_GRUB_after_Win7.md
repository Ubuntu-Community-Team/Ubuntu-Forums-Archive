---
title: "Can't Install GRUB after Win7"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by perito on 2010-01-07
so I have Ubuntu and I just installed Windows 7 on another partition. I then placed a LIVE CD to re-install grub, but its not working.
I can see my ubuntu partition, so everything is still there, but grub is not installing ...

first when I launched the terminal. 'grub' was unrecognized and I had to download it from the internet.
> grub> root(hdX,Y)

Error 27: Unrecognized command

grub> root (hdX,Y)

Error 23: Error while parsing number

grub> root(hdX,Y)

Error 27: Unrecognized command

grub> find /boot/grub/stage1

Error 15: File not found

grub> 


what should I do?

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfff0b24f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       10238    80696320    7  HPFS/NTFS
/dev/sda3           10239       10481     1951897+  82  Linux swap / Solaris
/dev/sda4           10482       19457    72099720   83  Linux
ubuntu@ubuntu:~$ 


---

### Post by philinux on 2010-01-07
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Also see the grub2 link below.\/

---

### Post by perito on 2010-01-07
> **philinux said:**
> [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Also see the grub2 link below.\/

Thanks

---

### Post by perito on 2010-01-07
ok something is wrong, I am able to see my old grub screen and log in to ubuntu normally, but now I cant go to the new windows 7 (even though I see it in the list), it says its linking to a wrong place.
I went into ubunutu (install version, not live) and terminal and tried to lanch grub but got

ubuntu@ubuntu-laptop:~$ sudo gedit /boot/grub/menu.lst (THIS WAS EMPTY)
ubuntu@ubuntu-laptop:~$ grub
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
grub: command not found
ubuntu@ubuntu-laptop:~$ 

Where is grub located and why I cant access it from my ubuntu?

---

