---
title: "GRUB not seeing Windows 7"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by marsgorski on 2011-06-03
Hi everyone. I had Ubuntu already in my computer and today I installed Windows 7 in a new partition. Then, I used Rescatux to restore GRUB and now I can boot into Ubuntu again. The problem now is that GRUB is not seeing my Windows  7 partition. How do I fix this? It seems I have to edit menu.lst but I  don't know how to do this. When I run sudo fdisk -l in the terminal I  get this:

Disk /dev/sda: 160.0 GB, 160041885696
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size  (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb1710f3

    Device      Boot           Start             End              Blocks       Id               System
/dev/sda1                            1          15313     122995680+      83               Linux
/dev/sda2       *             15313         18719        27364352         7               HPFS/NTFS
/dev/sda3                      18720         19457         5927985         5               Extended
/dev/sda5                      18720         19457          5927953+     82              Linux swap / Solaris

Thanks for any help

---

### Post by el_koraco on 2011-06-03
Just try 

```
sudo update-grub
```

---

### Post by marsgorski on 2011-06-03
Forgot to mention it. I did try that, and nothing seemed to change.

---

### Post by wojox on 2011-06-03
What does this show:

```
grub-install -v
```

---

### Post by marsgorski on 2011-06-03
It shows 'grub-install (GNU GRUB 0.97)'

---

### Post by wojox on 2011-06-03
You installed Grub Legacy. If you want Grub2 back have a look here [Copy LiveCD Files]("https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files")

---

### Post by marsgorski on 2011-06-03
Grub Legacy is what I had before installing Windows 7. I think the reason is because my first installation of ubuntu in this machine was back in 2009, and the newer versions of ubuntu came by updating, not clean installations. Anyway, I fixed the problem by adding 

```

title                 Windows 7
root                (hd0,1)
savedefault
makeactive
chainloader     +1

```

to the file menu.lst in the /boot/grub folder, as it was suggested in [this thread.]("http://ubuntuforums.org/showthread.php?t=175276")

Having fixed this problem is it still worth upgrading to GRUB2?

Thanks for the help.
[]("http://ubuntuforums.org/showthread.php?t=175276")

---

### Post by wojox on 2011-06-03
No chainloading is another option. I assumed you had Grub2 installed previously. Glad you got it running. :P

---

