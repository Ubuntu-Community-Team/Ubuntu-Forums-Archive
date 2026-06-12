---
title: "ubuntu desktop edition question"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by wozzroo on 2010-09-24
Hi,

A first time poster here, I have been using the forums for a while now to get tips and information on Wubi and Linux in general.

I installed Ubuntu 10.04 on windows 7 using Wubi and it would crash a lot, the screen would freeze, mouse also and could not do anything at all.

Installed and uninstalled Wubi several times, installed fine each time, but each time it would crash. I installed video drivers and updates and generally tried as many things as I could from the information I gathered here.

I then decided to try the desktop edition by downloading the ISO file to my USB and running it from there.

Chose the "run side by side " option when setting up the partition and allocated a few extra GB to the Ubuntu partition. It installed OK and then when I restarted, the Ubuntu partition is not in the the boot menu/ screen.

But when I put the USB back in and boot from it, it runs fine. Currently using the new installation and no crash as of yet.

So, my question is, do I have to boot the Ubuntu OS from the USB each time I want to use it ? or did I make a mistake.

Thanks.

I am a Linux noob btw, but love it :popcorn: 
Sorry about the long post.

---

### Post by jtarin on 2010-09-24
Do you get a Grub screen without the USB?

---

### Post by wozzroo on 2010-09-24
No screen, nothing without the USB, it just boots directly into Windows.

When I use the USB, i get 4 or 5 options e.g :

Ubuntu generic
Ubuntu... (recovery mode )
Ubuntu (sda.....)

No idea what the last one means :P

---

### Post by jtarin on 2010-09-24
Enter the command ```
sudo fdisk -l
``` in a terminal and post results. (with USB in , of course)

---

### Post by wozzroo on 2010-09-24
This is the output of fdisk

> 

woz@woz-laptop:~$ sudo fdisk -l

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcd7963e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb2             192       18154   144281787+   7  HPFS/NTFS
/dev/sdb3           18154       37486   155279361    f  W95 Ext'd (LBA)
/dev/sdb4           37486       38914    11471872   17  Hidden HPFS/NTFS
/dev/sdb5           30959       37486    52427776    7  HPFS/NTFS
/dev/sdb6           18154       30432    98624512   83  Linux
/dev/sdb7           30433       30959     4225024   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 4219 MB, 4219469824 bytes
2 heads, 63 sectors/track, 65405 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0184eee5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       65406     4120544+   b  W95 FAT32




---

### Post by jtarin on 2010-09-24
You will need to reinstall Grub to the MBR of /dev/sdb which is your hard drive.

---

### Post by wozzroo on 2010-09-24
Thanks for the reply.

I found some threads on reinstalling grub, but when I do : sudo grub,  I get : command not found.

Grub is there in the boot directory, it has a load of files in it. :confused:

---

### Post by jtarin on 2010-09-24
[Reinstall Grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")...scroll down to method #3 CHROOT follow instructions until you get to #9 it should be amended to your install as follows:```
Reinstall GRUB 2:
Substitute the correct device - sda, sdb, etc. Do not specify a partition number.
grub-install /dev/sdb
```Grub will complain and if it does re-issue the command adding -force as it will advise.
step #10 Skip...do not do.Complete the rest of the steps and reboot removing your USB. You should see the Grub screen._This will overwrite your Windows MBR_......make certain this is what you want before you proceed. My signature has an alternative way to boot Linux.

---

### Post by wozzroo on 2010-09-25
Just an update.

Well after several hours of trying to configure grub, I got it to work and then I kept getting the grub prompt every time I booted up. It would go directly to it.

So I could not boot to windows unless I booted from USB. The MBR was messed up.

Anyway, I got the Windows MBR back and it boots directly into Windows again from start up.

If i want to use Ubuntu, I have to boot from USB.

I think I will just use this method for a while until I become more familair with linux. Don't want to mess it up again.

:guitar: Thanks for your help.

---

### Post by jtarin on 2010-09-25
Is there any reason you cannot boot from an Ubuntu CD?

---

### Post by wozzroo on 2010-09-25
I don't have Ubuntu CD, just put a copy onto the USB, should I burn a copy to CD?

How can I tell where Ubuntu is mounted? I want to unmount it and then try to remount it and do the grub reinstall.

I realize I can't mount a drive in use. Any ideas how to go around it?

Thanks.

---

### Post by wozzroo on 2010-09-25
I used the EasyBCD on your signature and got the boot screen working.

So now I have a choice to boot into Windows or Linux.

If I boot to 7, it works.

If boot to Linux I get :

> 

Boot from (hd0,5) ext4  4e21......-.......-.....-....-............

error 15 File Not Found

grub>



Then I boot from USB.

---

### Post by wozzroo on 2010-09-25
Got it working.

Did : 

> 

sudo update-grub

 On the linux desktop.

Restarted and it displays

> 

 boot from (hd0,5) 4...-....-.....
 
 Starting up......


then it boots.

Thank you for your help, I owe you a beer. :popcorn:

---

### Post by jtarin on 2010-09-25
Boot Ubuntu. When you have a desktop remove the USB and run this command while in Ubuntu from the terminal. ```
fdisk -l 
```and post the results so we can determine exactly your Ubuntu partion number.

If we ignore the USB altogether you only have one drive.....it is normally /dev/sda and if go on that premise then your Linux partition is at /dev/sda6 but using EasyBCD it expects Grub2 to be installed at this location. If you have Grub installed at this location point EasyBCD at it. Make sure you select Grub2 in EasyBCD.If you have email I can send you 2 documents for setting up a dual boot...PM me with the address..

---

### Post by jtarin on 2010-09-25
> **wozzroo said:**
> Got it working.

Did : 

 On the linux desktop.

Restarted and it displays


then it boots.

Thank you for your help, I owe you a beer. :popcorn:Man I could use one today!:P

---

