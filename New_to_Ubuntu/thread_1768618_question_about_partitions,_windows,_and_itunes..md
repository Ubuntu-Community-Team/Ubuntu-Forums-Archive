---
title: "question about partitions, windows, and itunes."
date: 2011-05-27
forum: New to Ubuntu
---

### Post by Maksymillian on 2011-05-27
Hey all, I've been using Ubuntu for a few weeks now. I had meerkat for a few days and just got started with it before updating to narwhal (might as well, i was barely in the water with 10.10). Super impressed and super fun to be relearning an OS.

ANYWAYS.

In order to fully immerse myself I decided to go straight ubuntu on my laptop, no dual wielding ***** crap. I wiped everything from my disk drives to make an all ubuntu partition. I recently had a change of mind as to being *completely* windows independent.... what would be the best way to go about it?

Theres much documentation on setting up ubuntu from windows, but not so much the other way around.

q 1) Is my factory image on my compaq presario CQ56 still around? I don't think it is,  I assume it was part of a partition that got wiped..?

q 2) Would you recommend partitioning the HD and "recreate" a windows partition? I have very little experience with this part of windows but I'm getting the basics down.

q 3) anything else to be said?

Heres my fdisk output:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005fdca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37530   301454336   83  Linux
/dev/sda2           37530       38914    11114497    5  Extended
/dev/sda5           37530       38914    11114496   82  Linux swap / Solaris

edit* the thread title promised itunes... I basically need a fully functioning itunes for my iphone, something linux cant do thanks to steve jobs. It's not enough to stop me from delving deeper into ubuntu.

---

### Post by coffeecat on 2011-05-27
> **Maksymillian said:**
> q 1) Is my factory image on my compaq presario CQ56 still around? I don't think it is,  I assume it was part of a partition that got wiped..?

No. It got wiped. You have only Linux partitions on your 320GB drive. The first partition is a primary partition with your Ubuntu root partition - sort-of equivalent to a Windows C: 'drive'. The extended partition (sda2) is a container for the single logical partition which is your swap partition.

> **Maksymillian said:**
>  q 2) Would you recommend partitioning the HD and "recreate" a windows partition? I have very little experience with this part of windows but I'm getting the basics down.

Question is, what Windows install media do you have? If you have a set of Compaq restore discs, they will (probably) restore Windows back to the factory default, but in the process will (probably) overwrite everything on the hard drive. I can't be sure exactly what will happen because OEM manufacturer's restore discs vary in their flexibility, but I've not met one yet that will respect a pre-existing Linux installation.

If you don't have Compaq restore discs you would need to install Windows from a Microsoft retail install disc. In which case, since you only want to run iTunes on it, you might want to think about running Windows in a virtual machine within Ubuntu using something like VirtualBox or VMWare.

How old is that Compaq? Which version of Windows was it running? How much RAM?

---

### Post by quarkhirad on 2011-05-27
> **Maksymillian said:**
> Hey all, I've been using Ubuntu for a few weeks now. I had meerkat for a few days and just got started with it before updating to narwhal (might as well, i was barely in the water with 10.10). Super impressed and super fun to be relearning an OS.

ANYWAYS.

In order to fully immerse myself I decided to go straight ubuntu on my laptop, no dual wielding ***** crap. I wiped everything from my disk drives to make an all ubuntu partition. I recently had a change of mind as to being *completely* windows independent.... what would be the best way to go about it?

Theres much documentation on setting up ubuntu from windows, but not so much the other way around.

q 1) Is my factory image on my compaq presario CQ56 still around? I don't think it is,  I assume it was part of a partition that got wiped..?

q 2) Would you recommend partitioning the HD and "recreate" a windows partition? I have very little experience with this part of windows but I'm getting the basics down.

q 3) anything else to be said?

Heres my fdisk output:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005fdca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37530   301454336   83  Linux
/dev/sda2           37530       38914    11114497    5  Extended
/dev/sda5           37530       38914    11114496   82  Linux swap / Solaris

edit* the thread title promised itunes... I basically need a fully functioning itunes for my iphone, something linux cant do thanks to steve jobs. It's not enough to stop me from delving deeper into ubuntu.


Regrading q1 i think your image is wiped as normally these recovery  partitions are NTFS and their are no ntfs partitions  in your hdd. I have a  HP Dv600  laptop and my recovery partition is ntfs .  

One  more thing when i boot up my  laptop in grub menu i can choose  to  boot ubuntu or boot ubuntu in recovery mode or  boot memtest and after that there is an option to boot windows (i have windows) then there is a forth  option to boot  windows recovery (you  factory installed recovery  partition).                   

How many  options do you have?? if your recovery  partition is gone  then you will only have the first three options.

---

### Post by col48 on 2011-05-27
My one contribution to this thread is that, having read other peoples woes on many other threads on dual-booting......

If you choose to have a dual-boot rather than coffecat's idea of using a VM, install the Windows partition(s) first:  Windows does not respect Linux (especially the boot stuff) but Ubuntu respects Windows.


I like coffeecat's idea.  A VM is not such a big presence on your machine.

---

### Post by Maksymillian on 2011-05-27
awesomely fast responses :D

> **coffeecat said:**
> Question is, what Windows install media do you have?

... running Windows in a virtual machine within Ubuntu using something like VirtualBox or VMWare.

How old is that Compaq? Which version of Windows was it running? How much RAM?

I'm not at my home right now, I'll find out tomorrow if I got CDs with  this laptop.. I don't think I did, in which case I'll scope out what  compaq/HP has to offer in the way of that. I got this laptop earlier  this year as a strictly mobility/university work notebook, windows 7  (starter i believe, it def. wasnt a big or pro copy of win7), and 3.6gb  ram.

Originally I got wine, and can run a semi functioning bloated itunes and  I wasnt interested in that. I downloaded virtualbox recently but havent  gotten around to using it fully, as I'm still learning exactly how to  use it. I don't have high expectations with it and my USB-iphone  connection, or itunes. I'm still reading about whats possible and whats  not.

> **quarkhirad said:**
> How many  options do you have?? if your recovery  partition is gone  then you will only have the first three options.

I've had to restart ubuntu a couple times in the past in safe or previous kernel modes. No windows options.

---

### Post by LowSky on 2011-05-27
LOL... I love new Ubuntu users.. they are guaranteed to do two things, ask about iTunes and break a kernel image or two at some point.

Hey I've been there too. As for your iPhone  you will need iTunes, which means Mac OS/X or Windows. Banshee (the included music app) can add music to iPods but I'm not too sure about iPhones.

To be fair I have no idea why a smart phone needs a PC connection in the first place. My Android phone updates/Syncs and everything else straight from the air. Anyway... I use Win 7 all the time due to a bad gaming habit. Oddly I will boot out and use Ubuntu for everything else. It just feels right. If you can't get by on Linux, don't feel ashamed. Most of the people here can't, its only the annoying better than thou people who scream to only use Ubuntu or Linux in general.

---

### Post by coffeecat on 2011-05-27
> **Maksymillian said:**
> I'll find out tomorrow if I got CDs with  this laptop.. I don't think I did, in which case I'll scope out what  compaq/HP has to offer in the way of that. I got this laptop earlier  this year as a strictly mobility/university work notebook, windows 7  (starter i believe, it def. wasnt a big or pro copy of win7), and 3.6gb  ram.

I don't know about Compaq, but the machines I have experience of don't provide restore DVDs (they would be DVDs, not CDs with windows 7), but provide a software utility for you to create a set of DVDs. Since you don't have a set and your restore partition is gone, that option is closed to you, so you will have to contact Compaq. They will probably be prepared to sell you a set but they could be distressingly expensive.

If, by chance, you know of someone with the identical model, you could use that to prepare a set of restore DVDs. It would need to be identical, not similar. The Windows images are created by the manufacturers complete with the drivers for the particular hardware.

---

### Post by quarkhirad on 2011-05-28
> **Maksymillian said:**
> awesomely fast responses :D

I've had to restart ubuntu a couple times in the past in safe or previous kernel modes. No windows options.


Then buddy your recovery partition given by the factory is gone.You might be  able to recover the partition using partition magic's recovery  tool or any other equivalent software. However,i  really don't  know how much you can succeed in  recovering the partition  as i have never been fully successful in doing so.  could only recover some part of the data when  i  accidentally deleted one partition of my hdd. .

---

