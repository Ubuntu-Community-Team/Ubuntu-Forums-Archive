---
title: "Error after installation, no such device?"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Frustrateduser on 2009-11-29
I would like to apologize ahead of time, as I can imagine how frustrating all the newb problems must be. 
 
I've just decided to load ubuntu onto one of my older machines that has just been sitting around. I don't have much command line type knowledge and figured this might be an interesting project as I keep reading all these good things about ubuntu. I installed distro 9.10, as the only OS on the drive. After installation and reboot it gives me the GRUB menu. 
 
When I select Ubuntu Linux it just says;
 
error: no such device: 49312e42-80ea-4fe6-9593-9e469b28f87a
 
 
I've tried reinstalling it several times. I've also tried the 10.04 distro. same thing happens.
 
 
Any help, for real newbs, would be greatly appreciated. 
 
 
-FrustratedUser

---

### Post by Frustrateduser on 2009-11-29
Not sure if this helps. I'm able to boot into Ubuntu using the CD. If I were to choose intallation again, it asks to choose partition allocation, it shows that ubuntu is already installed across the whole drive. 
 
Thanks again all. Was really excited to give this a whirl, but it would seem the wind has been taken out of my sails. ;-)

---

### Post by Elfy on 2009-11-29
Can you open a terminal from the Apps Accessories menu of the live cd, run these commands and post the output here please.

```
sudo fdisk -l
ls -al /dev/disk/by-uuid
ls /boot/  /boot/grub/
```

Please use code tags around each output - that is put [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, make sure to use the [ and ] brackets

---

### Post by Frustrateduser on 2009-11-29
Thanks for the quick reply! 
I was thinking of just installing an earlier distro and seeing if that works. Just getting frustrated that i can't even get it to boot. haha, again thanks for the reply. Hope this speaks to you. 
 
```

[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] fdisk -1
fdisk: invalid option -- '1'
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```
 
 
 
```

[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] ls -al /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root  80 2009-11-29 12:28 .
drwxr-xr-x 6 root root 120 2009-11-29 12:28 ..
lrwxrwxrwx 1 root root  10 2009-11-29 12:27
49312e42-80ea-4fe6-9593-9e469b28f87a -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-11-29 12:28 E0FD-1813 -> ../../sdb1

```
 
 
 
```

[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] ls /boot/ /boot/grub/
/boot/:
abi-2.6.32-5-generic  config-2.6.32-5-generic  grub  memtest86+.bin
System.map-2.6.32-5-generic  vmcoreinfo-2.6.32-5-generic
/boot/grub/:
grubenv
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] 

```

---

### Post by Elfy on 2009-11-29
sudo fdisk -l


That is an L not a 1 ;)

Have another go - the last command while correct I should have not given you yet :)

So run the first again - in future if you get an error from a command that someone has shown you - try to copy and paste it instead.

---

### Post by Frustrateduser on 2009-11-29
Thanks, i'm trying to do this across two machines. The one i'm using to post here (windows based), and the one i'm trying to fix, which is currently booting off of the CD. I was going to try and email the commands back and forth but i'm having trouble gettinig gmail to work through Evolution.

---

### Post by Frustrateduser on 2009-11-29
```

ubuntu@ubuntu:~$ fdisk -l
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]

```
 
Thanks all it gives me, nothing more. :(

---

### Post by Kevbert on 2009-11-29
Please use
```
**sudo** fdisk -l

```
and post back.

---

