---
title: "How do I remove an XP partition?"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by blues2use on 2010-07-27
Running 2.6.32-24-generic on an XP/10.4 **dual boot** laptop.

My current 10.4 install is running great on my old Presario V2000 so I'd like to remove the XP partition and use the extra drive space for my existing 10.4 installation. From what I've read, I can do that using either the Live CD or my Gparted Live CD but how will that affect the grub2 boot process on /dev/sda1 ? If I delete that partition, will the grub2 boot record take a hike? 

Will I have to reinstall grub2 on /dev/sda1 via a Live CD or SuperGrub CD or will the grub2 OS Prober will know that XP is gone and still be able to boot to the grub boot menu choices without XP being on the menu?

**Here's my current disk info:**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5846    46957576+   7  HPFS/NTFS
/dev/sda2            5847        9730    31192065    5  Extended
/dev/sda5            5847        9592    30084096   83  Linux
/dev/sda6            9592        9730     1106944   82  Linux swap / Solaris

I'm hoping that someone has already done this and can give me some pointers as to the proper steps to take.

Thanks  :)

---

### Post by stlsaint on 2010-07-27
Im pretty sure that if your dual booting than ubuntu is on /dev/sda which in that case NO it will not be removed if you delete the windows partition. Now once you delete the partition you will need to run:
```
sudo update-grub
``` for grub to create a new grub.cfg that will not have the xp option of booting. If the worse happens than a simple install of grub back to /dev/sda MBR is all thats needed. Please see my link of grub2 in my signature if you have questions.

---

### Post by Elfy on 2010-07-27
Assuming that when you installed you let the installer deal with grub then I would just format the ntfs partition with gparted then run a grub update. You'll need to then deal with mounting the new partition.

There's no need to run either a buntu or gparted livecd here - in fact it is probably safer - no way to blitz the wrong partition, just make sure that the ntfs partition is unmounted.

You will need to install gparted if you want to do it from within ubuntu. 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by blues2use on 2010-07-27
> **forestpiskie said:**
> Assuming that when you installed you let the installer deal with grub then I would just format the ntfs partition with gparted then run a grub update. You'll need to then deal with mounting the new partition.

There's no need to run either a buntu or gparted livecd here - in fact it is probably safer - no way to blitz the wrong partition, just make sure that the ntfs partition is unmounted.

You will need to install gparted if you want to do it from within ubuntu. 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

So far, so good. Here's what the partitions look like now:

[IMG]http://i767.photobucket.com/albums/xx315/blues2use/Misc/gparted.jpg[/IMG]

How do I combine /dev/sda1 and /dev/sda5 into one large primary partition? Do I need to delete /dev/sda2 and, if so, how?


Thanks for the help...

---

### Post by bodhi.zazen on 2010-07-27
> **blues2use said:**
> How do I combine /dev/sda1 and /dev/sda5 into one large primary partition? Do I need to delete /dev/sda2 and, if so, how?

You have to boot a live CD and then do it in steps.

Open gparted.

Unmount your swap partition.

delete sda1

apply changes

make sda2 larger 

apply changes

make sda5 larger

apply changes.

You can not make all the changes in one step ;)

---

### Post by blues2use on 2010-07-27
> **bodhi.zazen said:**
> You have to boot a live CD and then do it in steps.

Open gparted.

Unmount your swap partition.

delete sda1

apply changes

make sda2 larger 

apply changes

make sda5 larger

apply changes.

You can not make all the changes in one step ;)

**Thanks for the reply.** I followed the steps and all went fine until reboot - all I get is a flashing cursor in the upper left corner of my screen. I thought that the boot flag wasn't set but, according to GParted, it is. Unsure what to do next...:shock: ... Please advise...

Thanks

---

### Post by antmenj on 2010-07-28
If you have an external drive or can install a second drive:

Load gparted from a systemrescucd

Copy the ubuntu partition to the external or other drive

Reinstall ubuntu on the computer main drive

Copy the ubuntu partition back in place of the new install then resize to maximum.

I'm sure there must be an easyer way but I'v done the about a few time and it worked.

---

### Post by Wim Sturkenboom on 2010-07-28
> **blues2use said:**
> So far, so good. Here's what the partitions look like now:

[IMG]http://i767.photobucket.com/albums/xx315/blues2use/Misc/gparted.jpg[/IMG]

How do I combine /dev/sda1 and /dev/sda5 into one large primary partition? Do I need to delete /dev/sda2 and, if so, how?


Thanks for the help...The easiest would have been to mount /dev/sda1 on a directory in /home; that way it's basically an extension of /home.
The next easiest would have been to use /dev/sda1 as the partition for /home.

But from post #6, this is to late now :(

---

### Post by Elfy on 2010-07-28
Try reinstalling grub - I'd guess it is looking for the old partition, the UUID would have changed after you expanded the install partition.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

