---
title: "I have 2 partitions, one XP one ubuntu, how can I choose @ startup between the 2?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by JohnParker on 2008-12-07
I successfully partitioned and install windows xp, but I can't find a way to  choose between the 2 at startup, apcmag's Guide DOES NOT WORK FOR ME.

---

### Post by lovelyvik293 on 2008-12-07
You installed the windows XP after the Ubuntu?
In this case you have to install the grub of ubuntu again.
It helps you
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by JohnParker on 2008-12-07
Yes xp was after ubuntu. I've already installed grub again, im on ubuntu right now, but I can't get to xp.

---

### Post by MarblePanther on 2008-12-07
burn supergrubdisk to a cd and boot it

EDIT:

ok youre in ubuntu

use synaptic to download startup-manager

use startup-manager to easily configure your grub conf

---

### Post by lovelyvik293 on 2008-12-07
All right just add the windows xp entry in the /boot/grub/menu.lst file.

---

### Post by JohnParker on 2008-12-07
I dont need the grub, grub is fine I can boot into ubuntu fine, its XP I can't boot into.

---

### Post by MarblePanther on 2008-12-07
GRUB is a bootloader--meaning you need it to be able to boot into Windows and Ubuntu

You do need it if you plan on dual-booting

Download startup-manager and use it


EDIT:

Go to /boot/grub and edit your menu.lst file to include windows first


EDIT2:

usually it is

Windows
makeactive
chainloader +1

More specifically:

title           Windows
rootnoverify    (hd#,#)            <---this being your hd and partition numbers (you can check this with gparted)
chainloader +1
makeactive
boot

---

### Post by lovelyvik293 on 2008-12-07
Please post the output from 
```
sudo fdisk -l
```

---

### Post by JohnParker on 2008-12-07
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43924392

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15415   123820956   83  Linux
/dev/sda2   *       15416       29645   114302475    7  HPFS/NTFS
/dev/sda3           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

---

### Post by lovelyvik293 on 2008-12-07
Add the following lines to /boot/grub/menu.lst
```

title		Windows XP
 root		(hd0,1)
 makeactive
chainloader	+1


```

---

### Post by JohnParker on 2008-12-07
Ok, I added, I am restarting now ill repost in a minute.

---

### Post by inxygnuu on 2008-12-07
these people already have it going, but you have to run
```
sudo gedit /boot/grub/menu.lst
``` then go to the end, and add what they said. oh, and for the people whom answered, will this work for vista/7? I reallyu want to get those Operating sytems up and running again.
My first code, yay!,
3v4n:)

---

### Post by inxygnuu on 2008-12-07
oops, posted too late, but how did it go?

---

### Post by lovelyvik293 on 2008-12-07
Yes it also works for vista.

---

### Post by lovelyvik293 on 2008-12-07
> **inxygnuu said:**
> oops, posted too late, but how did it go?
I don't get what you wanna ask??

---

### Post by inxygnuu on 2008-12-07
how the startup went.:)

---

### Post by inxygnuu on 2008-12-07
and while i have everyones attention, here is my output of "sudo fdisk -l"

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ddd1ddc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3882    31180800    7  HPFS/NTFS
/dev/sda3            3883       24321   164176267+   5  Extended
/dev/sda5            4266       15209    87907648+   7  HPFS/NTFS
/dev/sda6           19298       24321    40346624    7  HPFS/NTFS
/dev/sda7            3883        4265     3076384+  82  Linux swap / Solaris
/dev/sda8           15210       19297    32836828+  83  Linux

Partition table entries are not in disk order

Hoep i can fix it,
3v4n

---

### Post by JohnParker on 2008-12-07
Yay, it works. But to my not so surprise, Windows already has errors! Not enough disk space? orly? theres 99gigs mr windows.

---

### Post by inxygnuu on 2008-12-07
I don't know what to say, but mine has them too. It always says: "invalid device requested" and therefore, never works:(

With you here,
3v4n

---

