---
title: "Dual Booting"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by TKOP on 2009-06-07
[FONT=Trebuchet MS]I want to be able to dual boot from two separate hard drives. I already have one HD with Windows XP Prof. and one HD with Ubuntu. Does anyone know how to do this? All the stuff I've read on Dual Booting is for a single HD. It is a little annoying to open up the desktop case every time I want to switch between Win & Linux. Thanks.[/FONT]:D

---

### Post by LewRockwell on 2009-06-07
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Johan-Steyn on 2009-06-07
Hi,

Check out this guide to create a grub loader that will boot your XP & Ubuntu drives and allow you to choose between them, which you want to boot:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I hope it helps.

Regards,

JS

---

### Post by gamblor01 on 2009-06-07
> **TKOP said:**
> [FONT=Trebuchet MS]I want to be able to dual boot from two separate hard drives. I already have one HD with Windows XP Prof. and one HD with Ubuntu. Does anyone know how to do this? All the stuff I've read on Dual Booting is for a single HD. It is a little annoying to open up the desktop case every time I want to switch between Win & Linux. Thanks.[/FONT]:D
This is very simple to accomplish.  The file /boot/grub/menu.lst controls what operating systems can be booted, and which partitions they reside on.  So we just need to properly setup your menu.lst.

First, can you run the following command in Ubuntu and post the results?  It will tell us how your hard drives are configured, partitioned, and formatted:

```

sudo fdisk -l

```

---

### Post by Miljet on 2009-06-07
The one point that most how-tos fail to make clear is where to install GRUB. It has to be installed to the MBR of whichever disk boots first. If your Windows disk is the first to boot, you would install GRUB to the MBR of that disk and it would point to the menu.lst file on the other disk. Or if the Ubuntu disk is the first to boot, install GRUB to the MBR of that disk and point it to the same disk.

---

### Post by ayenack on 2009-06-07
> **Miljet said:**
> The one point that most how-tos fail to make clear is where to install GRUB. It has to be installed to the MBR of whichever disk boots first. If your Windows disk is the first to boot, you would install GRUB to the MBR of that disk and it would point to the menu.lst file on the other disk. Or if the Ubuntu disk is the first to boot, install GRUB to the MBR of that disk and point it to the same disk.

+1

Make sure you intall GRUB to the right drive.

During the Ubuntu install it gives you the option where to install GRUB make sure that it's installed to your boot dive which I'm guessing will be the Win XP drive.

---

### Post by TKOP on 2009-06-09
Thanks guys. I will follow those instructions and let you know. I will post the results from fdisk soon.

---

### Post by nandemonai on 2009-06-09
As a side note, there should be no need to swap over plugs on the HDDs to change boot order. You can do that in BIOS, even on ancient machines.

---

### Post by LewRockwell on 2009-06-09
> **nandemonai said:**
> As a side note, there should be no need to swap over plugs on the HDDs to change boot order. You can do that in BIOS, even on ancient machines.

of course, the above statement is only accurate if the jumpers are already set correctly and your BIOS "sees" all drives properly...

then...yes, boot order can be selected via BIOS...

as always, your mileage may vary depending on your personal driving habits...

Never give up, never surrender!

---

### Post by TKOP on 2009-06-09
OK guys here's the printout from when I ran fdisk -l for your information.

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07e1145a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14570   117033493+  83  Linux
/dev/sda2           14571       14946     3020220    5  Extended
/dev/sda5           14571       14946     3020188+  82  Linux swap / Solaris

---

### Post by gamblor01 on 2009-06-09
> **TKOP said:**
> OK guys here's the printout from when I ran fdisk -l for your information.

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07e1145a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14570   117033493+  83  Linux
/dev/sda2           14571       14946     3020220    5  Extended
/dev/sda5           14571       14946     3020188+  82  Linux swap / Solaris
Hmm...are you sure this is the full output?  According to this it only knows of one drive, which is 123GB in size.  There should be a second hard drive there with an NTFS formatted partition, right?

---

### Post by ajgreeny on 2009-06-10
I suspect you had disconnected the windows drive to boot ubuntu- am I correct?  If so, connect it again, but don't disconnect the ubuntu drive, just boot the ubuntu live CD and run the sudo fdisk -l command again from that, when hopefully both disks will show up in the output.  Then we can start to put you right.

---

### Post by themacedonian on 2009-06-10
I have same problem. I hope that i will solve when this threat will close.
thanks people

---

### Post by themacedonian on 2009-06-11
chenge location
```
cd /boot/grub
```

backup menu.lst
```
sudo cp menu.lst menu.lst_backup
```

open menu.lst
```
sudo gedit menu.lst
```

add this:
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```
there


i made this and i have menu for choise os.

my problem happen when i click enter under WINDOWS .... i see error :S

some idea for solving my problem ?  :o

---

### Post by Bearly Able on 2009-06-11
I had a similar problem when I first installed Ubuntu.  In my case, I never could get GRUB to load XP, but the XP boot loader will launch GRUB, so I can still choose between OSs at bootup.

The thread that got my system up and running is [here]("http://ubuntuforums.org/showthread.php?t=1060203").  The original attempt was to load XP from GRUB, so that might work for you; if not, read on and try the other way!

---

### Post by TKOP on 2009-06-12
Ajgreeny you are right. I had unplugged my WinXP drive and plugged in my Ubuntu. ;)
I will go back boot of the Live CD and then with both drives plugged in post the fdisk -l results. :D

---

### Post by kansasnoob on 2009-06-12
It would also be helpful to know if the two drives are both IDE, both SATA, or a combination of the two.

---

