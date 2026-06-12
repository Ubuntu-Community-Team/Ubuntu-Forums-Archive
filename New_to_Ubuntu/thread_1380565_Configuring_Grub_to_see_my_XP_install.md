---
title: "Configuring Grub to see my XP install"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by Devilham on 2010-01-13
Hello, brand new user (I registered awhile back, and dabbled, but am now going all in), and installed Ubuntu 9.10 onto a seperate HD, HD0 being my XP install, HD1 the Ubuntu.  After installation, Grub seems to not see my XP install?  Any thoughts on how to clear this up?  I need my XP for multiple reasons.

---

### Post by corncob on 2010-01-13
First thing I'd do is to open Applications > Accessories > Terminal and type
```
sudo update-grub
```
If that doesn't work, post the output to see if it might tell us something.

---

### Post by Devilham on 2010-01-13
Tried that, it doesn't seem to work, where would I find the output, or do you mean the following...

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by Nuzair on 2010-01-13
Try to install grub2..maybe it can fix the problem..

go to terminal and type:

```
sudo apt-get install grub2
```then, try to update the grub

```
sudo update-grub2
```

---

### Post by Devilham on 2010-01-13
Seems to me Ubuntu is having troubles mounting the volume (I can't see the NTFS partition, and as I understand it, I should).  I think I need to run chkdsk /f out of windows, but that's just it, can't get to windows.  trying to think of a way to get to even DOS just to run the command on the volume.

---

### Post by tom.swartz07 on 2010-01-13
Okay- rather than updating, lets try a re-install of Grub.

Grab a liveCD and boot to it.

In a terminal, type this;

```
sudo fdisk -l
```


it should output something like this:
```
tom@ubuntu-karmic:~$ sudo fdisk -l
[sudo] password for tom: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       11904    85064175    7  HPFS/NTFS
/dev/sda4           11905       38913   216949792+   f  W95 Ext'd (LBA)
/dev/sda5           19233       19558     2618595   dd  Unknown
/dev/sda6           11905       18723    54773554+  83  Linux
/dev/sda7           18724       19232     4088511   82  Linux swap / Solaris
/dev/sda8           22979       24571    12795741   83  Linux
/dev/sda9           24572       36181    93257293+   7  HPFS/NTFS

Partition table entries are not in disk order
tom@ubuntu-karmic:~$ 

```

What you need to do is mount each of your partitions that you need to boot from, using this output.

```
sudo mount /dev/sdXY /mnt
```
where XY is each partition, for example sda2, sdb3,
You need to mount EVERY partition that you have an OS on. 

As a reference, in my output, I would mount sda3, sda6, and sda8.

After that, you need to install Grub:
```
sudo grub-install --root-directory=/mnt/ /dev/sdX
``` where X is the main drive that you use. Probably sda.


After it runs, you should be all set!

---

### Post by mattbutsko on 2010-01-13
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

Head there, scroll down to the pic that says END DEBIAN AUTOMAGIC KERNELS LIST. This page shows you how to edit the GRUB and add Windows XP manually. Should work just fine, done it many times. It does say Vista on the site, but it works with XP as well.

If possible, use the original GRUB, not Grub2. I believe Grub2 makes it a little harder, or trickier, or something like that, to edit the file.

---

### Post by garyed on 2010-01-13
I wouldn't do anything with windows yet. 
Post the output from the terminal of:
```
sudo fdisk -l
```

---

### Post by Devilham on 2010-01-13
here is my output 

devilham@devilham-ubuntu-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0d2d0d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd14cd14c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29319   235504836   83  Linux
/dev/sdb2           29320       30401     8691165    5  Extended
/dev/sdb5           29320       30401     8691133+  82  Linux swap / Solaris

---

### Post by Devilham on 2010-01-13
This is what I get when I try to mount the volume through the terminal

devilham@devilham-ubuntu-desktop:~$ sudo mount /dev/sda1 /mnt

ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by Devilham on 2010-01-13
Okay, here is what I think has gone wrong.  I had a machine set to dual boot to XP and Vista.  I hated Vista, so I downloaded Ubuntu, reformatted the drive that Vista was on, and installed Ubuntu to that drive.  I think that Vista's bootloader had taken over the job of boot.ini in windows XP, and since I just deleted it, that is what's screwing things up.  I don't expect anyone here to have a solution to a windows problem (I will start my research on that tomorrow), but if anyone knows a way to shoe horn in XP into Ubuntu's bootloader, it would certainly help, thanks!

---

### Post by garyed on 2010-01-14
You can make a custom entry for Grub to boot Windows.
If your Windows boot files are still in tact it will work, it doesn't sound very likely but its worth a shot.
Boot into Ubuntu,
Paste the contents below into a text file & name it " 72_custom "
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.
# Be careful not to change the 'exec tail' line above.
menuentry "Microsoft Windows" {
insmod ntfs
set root=(hd0,1)
drivemap -s (hd0) ${root}
chainloader +1
}

```
Go to the terminal & to the folder where 72_custom is & do:
```

sudo cp 72_custom /etc/grub.d/

```
then do:
```

sudo chmod 755 /etc/grub.d/72_custom

```
then do:
```

sudo update-grub

```
When you reboot Windows should be on the bottom of your grub menu & hopefully will boot it also. If not there is a way to put the Windows boot files back but that's as much as I know.

---

### Post by halitech on 2010-01-14
you could try Super Grub boot disk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

