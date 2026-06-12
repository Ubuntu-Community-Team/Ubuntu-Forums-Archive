---
title: "Mounting multiple USB drive problems"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by FMDCER on 2009-06-22
Can anyone help me please !

I am having trouble mounting a 40 meg Iomega external USB drive alongside a 1 T Fantom Drive (USB also). The computer will not `automount'

I have to manually mount each drive via sudo mount command and when all three are connected, the 1T drive suddenly takes on the Iomega's data 

Here is the device list per fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa77ea77e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7015    56347956   83  Linux
/dev/sda2            7016        7297     2265165    5  Extended
/dev/sda5            7016        7297     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74e849aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        4863    18579172+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000098ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

---

### Post by bodhi.zazen on 2009-06-22
flash drives auto mount for most people just fine.

Give each drive a label perhaps. I call my flash drive BUDDHA and it auto mounts at 

/media/BUDDHA

Other then general advice, are you using a server (no gui), gnome, KDE, xubuntu, other window manager ?

---

### Post by DGortze380 on 2009-06-22
> **FMDCER said:**
> Can anyone help me please !

I am having trouble mounting a 40 meg Iomega external USB drive alongside a 1 T Fantom Drive (USB also). The computer will not `automount'

I have to manually mount each drive via sudo mount command and when all three are connected, the 1T drive suddenly takes on the Iomega's data 

Here is the device list per fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa77ea77e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7015    56347956   83  Linux
/dev/sda2            7016        7297     2265165    5  Extended
/dev/sda5            7016        7297     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74e849aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        4863    18579172+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000098ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

I don't have a solution to your automount issue, but can you please post the commands you're using to mount the drives. It appears you're mistakenly mounting two drives to the same location.

---

### Post by FMDCER on 2009-06-22
> **bodhi.zazen said:**
> flash drives auto mount for most people just fine.

Give each drive a label perhaps. I call my flash drive BUDDHA and it auto mounts at 

/media/BUDDHA

Other then general advice, are you using a server (no gui), gnome, KDE, xubuntu, other window manager ?
The system is Xubuntu 9.04 and I think (can't remember all that I did) I used the following:

sudo mount all/dev/sdb1/sdb2/sdc1 /mnt

When I enterd, it never really gave any error so I thought it was OK. I guess not

---

### Post by FMDCER on 2009-06-22
> **bodhi.zazen said:**
> flash drives auto mount for most people just fine.

Give each drive a label perhaps. I call my flash drive BUDDHA and it auto mounts at 

/media/BUDDHA

Other then general advice, are you using a server (no gui), gnome, KDE, xubuntu, other window manager ?
How do you rename a flash drive or other usb storage device ?

---

### Post by merlin_ie on 2009-06-22
not sure if this will help much FMDCER but this is how I change name of drive to show in conky :  right click on drive, go to properties, in volume tab you'll see " Settings "..then you can configure a mount point. it will say /media/YOURDRIVE. Replace YOURDRIVE with whatever you want and then unmount drive. Next time you mount it, it will recognize the new name. Hope this helps

---

### Post by DGortze380 on 2009-06-22
> **FMDCER said:**
> The system is Xubuntu 9.04 and I think (can't remember all that I did) I used the following:

sudo mount all/dev/sdb1/sdb2/sdc1 /mnt

When I enterd, it never really gave any error so I thought it was OK. I guess not

ok. using the command above as reference (verify the /dev portions are correct for your device) you would want to use the following to mount the drives.

Each needs it's own location, so first.

```

sudo mkdir /mnt/myUSB1

```

```

sudo mkdir /mnt/myUSB2

```

```

sudo mkdir /mnt/myUSB3

```

then mount each drive to their respective folders

```

sudo mount /dev/sdb1 /mnt/myUSB1

```

```

sudo mount /dev/sdb2 /mnt/myUSB2

```

```

sudo mount /dev/sdc1 /mnt/myUSB3

```

As I suspected, you were trying to mount multiple drives to the same folder.

As for your automount issue. I suspect XFCE does not support automounting by default if at all ... though I could be wrong. Haven't run it in a while.

---

### Post by bodhi.zazen on 2009-06-22
> **FMDCER said:**
> How do you rename a flash drive or other usb storage device ?

Hmm ... I use xubuntu and auto mounts work.

Looking at your command it appears you are mounting devices at /mnt

First you need a unique mount point for each device.

Second nothing wrong with mounting in /mnt, auto mounting usually mounts in /media

Labeling a file system is dependent on the file system, it is different for FAT and ext3 ...

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")  

There is a section on labeling in the fstab page.

And the wiki :

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by bodhi.zazen on 2009-06-22
> **DGortze380 said:**
>  As for your automount issue. I suspect XFCE does not support automounting by default if at all ... though I could be wrong. Haven't run it in a while.

Well, XFCE is a window manager ;)

Thunar supports automounting.

---

### Post by DGortze380 on 2009-06-22
> **bodhi.zazen said:**
> Well, XFCE is a window manager ;)

Thunar supports automounting.

True, i misspoke. thanks.

---

### Post by bodhi.zazen on 2009-06-22
Sorry, I did not mean to be harsh. I was trying to pass on the information that Thunar supports auto mounting removable devices is all. 

I apologize if I came across the wrong way.

---

### Post by FMDCER on 2009-06-22
Thanks to everyone for your comments and suggestions. I'll try them (carefully) and get back with the results as soon as I can 

Many thanks !

Ben (FMDCER)

---

### Post by DGortze380 on 2009-06-22
> **bodhi.zazen said:**
> Sorry, I did not mean to be harsh. I was trying to pass on the information that Thunar supports auto mounting removable devices is all. 

I apologize if I came across the wrong way.

Of course not. Totally fine. Always want accurate information archived.

---

### Post by FMDCER on 2009-06-26
Update: I tried to install the recommendations (via command line) but the more I tried, the worse it got. In the end, I had to re-install Xubuntu (not before backing up all significant data first)

Thanks

Keep in touch !

Ben

---

### Post by cmcanulty on 2009-09-21
This is one area where windows has it all over Ubuntu, you plug in a USB device and it is there and totally accessible. Is there any tutorial on this topic. There is so much to learn and understand. I tried renaming my flash drive, unmounted and remounted as the above instructions say but the name didn't change.At least it is usually recognized but my 500GB ext hard drive shows and disappears all the time and the several Ubuntu backup programs I have tried never find it even when it shows as mounted under properties.Consequently I can't backup which makes me very nervous as I have 78GB of valuable music scores I can't lose.

---

