---
title: "I have a bad error, I think its a drive failure"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Kedster on 2008-12-15
ok so it not my comp im trying to fix my friends he had a hard crash(i dont think it was the first) and i couldn't recover it. I tried to reinstall and keep his home partition, that didn't work when i booted i got this error
```
Boot from (hd0,0) ext2 4391e1d9-a5ee-4e31-ad73-8a2cec42a48b
Starting up ...
[    0.004000] Aperture beyond 4GB. Ignoring.
loading, please wait...
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   -Check rootdelay= (Did the system wait long enough?)
   -Check root= (Did the system wait for the right device?)
 -Missing modules (cat /proc/proc: Is /dev)
ALERT! /dev/disk/by-uuid/4391e1d9-a5ee-4e31-ad73-8a2cec42a48b does not exist. Dropping to shell!


Busy box v1.10.2 (ubuntu 1:1.10.2-ubuntu6) built-in shell(ash)
Enter 'help' for a  list of built-in commands.

(initramfs) [    35.733317] 8139cp 0000 :08 :02.0: This (id 10ec : 8139 rev 10) is not an 8139c+ compatible chip
[    35.733366] 8139cp 0000 :08 :02.0: Try the "8139too" driver instead
```

so I took the drive out and I got all the personal data off of it as I could. I used an external hook up, some data was corrupt and it was very finiky as in i would like not be there sometimes and then show up that when i started to think the drive was bad. so I got what i could, then  formated the whole drive and did full reinstall. When i booted I got the same error. Am I correct about his drive being shot, or can i fix it.

---

### Post by Michael.Godawski on 2008-12-15
In my opinion the drive is nuked.

But perhaps some magicians will rescue it... :p

---

### Post by Viranh on 2008-12-15
A utility to test for a bad hard drive was suggested to a user in this thread:

[http://ubuntuforums.org/showthread.php?t=1007318](http://ubuntuforums.org/showthread.php?t=1007318)

The user had an error message similar to yours I believe. I would guess that the hard drive is probably bad, but it's probably worth checking it since utilities exist for this purpose. No need to replace something that isn't broken.

If the drive won't boot, I believe you can check it with something on this disk:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by bumanie on 2008-12-15
Most of the hard drive manufacturers have a download-able .iso live cd that you can burn and then check your hard drive with. It's probably the best bet, as the manufacturer should know more than anyone else about their own product.

---

### Post by karlr42 on 2008-12-15
> ```
Boot from (hd0,0) ext2
```
Why ext2? The default is ext3.
Also, I don't think the hard drive is necessarily damaged, it looks like grub is trying to boot from the wrong partition, which is easily solved.

---

### Post by Kedster on 2008-12-16
how do I solve the wrong boot drive prob in grub

---

### Post by bumanie on 2008-12-16
If karlr42 is correct, post the output of > sudo fdisk -lu from a live cd

---

### Post by spadhawk on 2008-12-17
output from sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5f81be65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39969719    19984828+  83  Linux
/dev/sda2        39969720   156296384    58163332+   5  Extended
/dev/sda5        39969783   145147274    52588746   83  Linux
/dev/sda6       145147338   156296384     5574523+  82  Linux swap / Solaris

---

### Post by bumanie on 2008-12-17
The drive shows partitions are setup correctly. Try a filesystem check > sudo fsck /dev/sdabut it's starting to look as though the drive is past its best. Try the drive  manufacturers site as suggested for their down-loadable tool. Also if the motherboard supports S.M.A.R.T enable that; it checks hard drives for errors (I think) - I have not used it so can't explain much about it, just know of it.

---

### Post by spadhawk on 2008-12-17
here is the output for fsck

fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?

nothing else is running

---

### Post by Michael.Godawski on 2008-12-17
> Code:
 	```
sudo touch /forcefsck
``` 
The way I do it is to type the above code into a terminal and then reboot my computer. When the computer is re-booting, if you watch carefully, you will see it pause during the boot-up sequence and do the fsck for you before it fininshed booting, that way the filesystem isn't mounted yet I presume. It looks like this (Below)
|============================                                          /

You will see the white '=' signs progress across the black screen until they reach the tumbling bar '/'. Sometimes it might stop and announce it has found a problem and fixed it. (It will often give details). 
Ubuntu will do an fsck automatically every thirty reboots anyway, you don't have to do it manually, but it shouldn't do any harm and might do some good.:grin: (Herman)
by [Herman]("http://ubuntuforums.org/member.php?u=31861")

---

### Post by spadhawk on 2008-12-20
i replaced the hd and have the same error
code:


Boot from (hd0,0) ext3 ae6e00e3-4438-463a-861b-ce88fe8876e7
Starting up ...
[    0.004000] Aperture beyond 4GB. Ignoring.
loading, please wait...
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   -Check rootdelay= (Did the system wait long enough?)
   -Check root= (Did the system wait for the right device?)
 -Missing modules (cat /proc/proc: Is /dev)
ALERT! /dev/disk/by-uuid/4391e1d9-a5ee-4e31-ad73-8a2cec42a48b does not exist. Dropping to shell!


Busy box v1.10.2 (ubuntu 1:1.10.2-ubuntu6) built-in shell(ash)
Enter 'help' for a  list of built-in commands.

(initramfs) [    35.733317] 8139cp 0000 :08 :02.0: This (id 10ec : 8139 rev 10) is not an 8139c+ compatible chip
[    35.733366] 8139cp 0000 :08 :02.0: Try the "8139too" driver instead

anybody have any ideas?

---

### Post by spadhawk on 2008-12-23
Hi Guys 
Merry Christmas

i'm really stumped here i have tried all suggestions. tried a new hard drive
new ram and still the same error coming up. i used the ultimatebootdisk and didnt find any errors.
could there be something in the bios doing this?
could it be the mb . the weird thing is that it will run the live cd , what could possibly be wrong with this machine?
this is the error i am getting


Boot from (hd0,0) ext3 ae6e00e3-4438-463a-861b-ce88fe8876e7
Starting up ...
[ 0.004000] Aperture beyond 4GB. Ignoring.
loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
-Check rootdelay= (Did the system wait long enough?)
-Check root= (Did the system wait for the right device?)
-Missing modules (cat /proc/proc: Is /dev)
ALERT! /dev/disk/by-uuid/4391e1d9-a5ee-4e31-ad73-8a2cec42a48b does not exist. Dropping to shell!


Busy box v1.10.2 (ubuntu 1:1.10.2-ubuntu6) built-in shell(ash)
Enter 'help' for a list of built-in commands.

(initramfs) [ 35.733317] 8139cp 0000 :08 :02.0: This (id 10ec : 8139 rev 10) is not an 8139c+ compatible chip
[ 35.733366] 8139cp 0000 :08 :02.0: Try the "8139too" driver instead


any help would be greatly appreciated

---

### Post by shad0w_walker on 2008-12-23
It looks like it cannot find the root partition for your system. If you've reinstalled to a new drive and not mirrored the old one, then your partitions UUID will have changed.

Do you have the livecd still available? If you do, boot into it and open a terminal (Applications > Accessories > Terminal) and then you will need to mount the partition your system is installed to. By the looks of it you will need to run these commands:

```

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1

```

This will mount your system partition in /media/sda1. Now you need to edit your fstab file to tell it the new UUID for your partition. This command should do the trick.

```
gksu gedit /media/sda1/etc/fstab
```

You should get a gedit window open with your fstab file in it. There will be a line in it that starts something like: 

```
UUID=4391e1d9-a5ee-4e31-ad73-8a2cec42a48b
```

You need to change the UUID specified there for the new one on your system. If I have read your other posts correctly, you should need to change it to read:

```
UUID=ae6e00e3-4438-463a-861b-ce88fe8876e7
```

Save the file and close gedit. Now shutdown and try to load Ubuntu again, hopefully things will be going again.

Good luck.

---

