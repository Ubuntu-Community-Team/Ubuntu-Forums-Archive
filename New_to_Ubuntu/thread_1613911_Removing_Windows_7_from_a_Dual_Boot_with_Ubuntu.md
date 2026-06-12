---
title: "Removing Windows 7 from a Dual Boot with Ubuntu"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by nns2006 on 2010-11-05
Hi,
I am trying to remove windows 7 from my system which is dual boot with Ubuntu 10.10
My ubuntu is installed on a separate partition. What should I do? I am afraid of doing this as it might create problem for my Ubuntu system. I don't want to loose my Ubuntu in [COLOR="Black"]**any possible way.**[/COLOR] . 
So, I request you to advise me for  uninstalling Windows 7. 

If you need any other information, I will be happy to provide.

Thank you.
Regards

Nitya

---

### Post by karthick87 on 2010-11-05
Install Gparted-Partition Manager in ubuntu.Open Gparted unmount your NTFS partition which has windows 7 and then delete the windows partition.Finally update your Grub entry.


To Install Gparted

```
[COLOR=Red]sudo apt-get install gparted[/COLOR]
```To Update Grub
[COLOR=Red]
[/COLOR]```
[COLOR=Red]sudo update-grub[/COLOR]
```

---

### Post by NightwishFan on 2010-11-05
First off, ensure you want to do this. :) When you have made a decision, it is actually quite simple.

First, back up all data you want to save to your Ubuntu partition. After you do that, load up an Ubuntu live cd. (Not install, just the live session). Using System -> Administration -> Gparted you can remove the Windows NTFS partitions, and extend the Ubuntu partition. This might take a while, DO NOT interrupt it prematurely. (Dire consequences await).

When you boot into Ubuntu again, you should run this command:
```
sudo update-grub
```

**NOTICE:**
I last did this in 2007, so I am not sure if there is anything to worry about or some caveat to my instructions, so please wait for someone else to confirm before you follow. :)

---

### Post by wilee-nilee on 2010-11-05
Since you have Ubuntu installed, install gparted and take a screenshot of it to confirm your partitioning setup. I have seen people dual boot and partition a wubi install so I personally want to rule this out.

If you have a real dual boot and Grub is the bootloader then it is fairly easy to do really. The resizing of the Ubuntu partition though if you decide to do so may cause a need to reload grub to the mbr.

Many in this situation if windows is at the front of the HD will just put a partition back in place for a separate home rather then resizing Ubuntu. I don't do that but if this is of interest to you just mention it in the thread, many do this and can help.

Personally I would keep the Windows back up imaged onto a HD or just shrink it small, basically protecting your investment.

---

### Post by nns2006 on 2010-11-05
Suppose I  selected the partition using gparted and format it (which one? ntfs again?) will it be same action or different than deleting. I think after deleting i will have to make a partition again. (guessing only)

---

### Post by karthick87 on 2010-11-05
Post your output,

```
 sudo fdisk -l
```

---

### Post by nns2006 on 2010-11-05
> **wilee-nilee said:**
> Since you have Ubuntu installed, install gparted and take a screenshot of it to confirm your partitioning setup. I have seen people dual boot and partition a wubi install so I personally want to rule this out.

If you have a real dual boot and Grub is the bootloader then it is fairly easy to do really. The resizing of the Ubuntu partition though if you decide to do so may cause a need to reload grub to the mbr.

Many in this situation if windows is at the front of the HD will just put a partition back in place for a separate home rather then resizing Ubuntu. I don't do that but if this is of interest to you just mention it in the thread, many do this and can help.

Personally I would keep the Windows back up imaged onto a HD or just shrink it small, basically protecting your investment.

Below I am attaching my gparted screenshot.

---

### Post by nns2006 on 2010-11-05
> **getyourkarthick said:**
> Post your output,

```
 sudo fdisk -l
```

This is the output.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        6534    52436160    7  HPFS/NTFS
/dev/sda3            6535       19457   103803233+   f  W95 Ext'd (LBA)
/dev/sda5            6535       13196    53510144    7  HPFS/NTFS
/dev/sda6           19196       19457     2104483+  dd  Unknown
/dev/sda7           13196       13702     4057088   82  Linux swap / Solaris
/dev/sda8           13702       19195    44129280   83  Linux

Partition table entries are not in disk order

---

### Post by nns2006 on 2010-11-05
> **wilee-nilee said:**
> .........

Many in this situation if windows is at the front of the HD will just put a partition back in place for a separate home rather then resizing Ubuntu. I don't do that but if this is of interest to you just mention it in the thread, many do this and can help.

I don't want to extend the Ubuntu partition size, rather I would like to keep it as a separate partition (the one on which W7 is installed). This is what you are saying or I misunderstood you?

---

### Post by karthick87 on 2010-11-05
Is it a laptop or desktop..?

Looks like you have your windows installed in this partition..
```

/dev/sda2   *           7        6534    52436160    7  HPFS/NTFS
```

Delete the partition using Gparted..

---

### Post by nns2006 on 2010-11-05
> **getyourkarthick said:**
> Is it a laptop or desktop..?

Looks like you have your windows installed in this partition..
```

/dev/sda2   *           7        6534    52436160    7  HPFS/NTFS
```

Delete the partition using Gparted..

Dell  laptop: Vostro 1500.

---

### Post by karthick87 on 2010-11-05
I think deleting your windows partition might damage your recovery partition.So that you cant get back your windows 7 i guess..

---

### Post by wilee-nilee on 2010-11-05
> **nns2006 said:**
> I don't want to extend the Ubuntu partition size, rather I would like to keep it as a separate partition (**the one on which W7 is installed**). This is what you are saying or I misunderstood you?

This is why I ask specific questions and want actual pictures or information. Your Ubuntu in its own partition that is great, and there is a ntfs partition sda5 in the extended partition. It is just a matter of understanding what your saying.

Now does that ntfs partition sda5 contain any operating part of Windows or is it just data like media, documents etc.

Everybody wants to jump on getting things deleted here without some pertinent areas being covered.

---

### Post by nns2006 on 2010-11-05
> **getyourkarthick said:**
> I think deleting your windows partition might damage your recovery partition.So that you cant get back your windows 7 i guess..

I dont have recovery partition. I have installed it using DVD and Its backup is in external hard drive.

---

### Post by nns2006 on 2010-11-05
> **wilee-nilee said:**
> This is why I ask specific questions and want actual pictures or information. Your Ubuntu in its own partition that is great, and there is a ntfs partition sda5 in the extended partition. It is just a matter of understanding what your saying.

Now does that ntfs partition sda5 contain any operating part of Windows or is it just data like media, documents etc.

Everybody wants to jump on getting things deleted here without some pertinent areas being covered.


That partition /dev/sda5  is a separate one used for keeping common data.

---

### Post by wilee-nilee on 2010-11-05
> **nns2006 said:**
> That partition /dev/sda5  is a separate one used for keeping common data.

Great I was just concerned since you want to lose nothing, and it sounds like your not backed up to a HD with the computers HD image.

I think your safe to delete sda2 and sda1, use the live Ubunbtu cd use gparted and turn off the swap when you do this by right clicking on it.

The only other odd part is the 200mib partition sda6 at the end in the gparted picture, what is that?

As long as Grub2 is the bootloader as of now it seems safe to delete these two partitions. 

You will have a unallocated space so I'm curious what your plans are.

I also assume that you know what works in Ubuntu that is in that common data sda5 partition.

---

### Post by nns2006 on 2010-11-05
> **wilee-nilee said:**
> Great I was just concerned since you want to lose nothing, andit sounds like your not backed up to a HD with the computers HD image.

I think your safe to delete sda2 and sda1, use the live Ubunbtu cd use gparted and turn off the swap when you do this by right clicking on it.

The only other odd part is the 200mib partition sda6 at the end in the gparted picture, what is that?

As long as Grub2 is the bootloader as of now it seems safe to delete these two partitions. 

You will have a unallocated space so I'm curious what your plans are.

I also assume that you know what works in Ubuntu that is in that common data sda5 partition.


Is use of Live CD essential? I have installed gparted. 
I will have to turn off swap by right clicking in gaprted, am I right? By the way what is the reason behind it? 

By Unallocated space do you mean the partitioned space or the one which is not used and written as unallocated? 
For the partition I will make new partition, so that I can install W7 in future if needed.

---

### Post by wilee-nilee on 2010-11-05
> **nns2006 said:**
> Is use of Live CD essential? I have installed gparted. 
I will have to turn off swap by right clicking in gaprted, am I right? By the way what is the reason behind it? 

By Unallocated space do you mean the partitioned space or the one which is not used and written as unallocated? 
For the partition I will make new partition, so that I can install W7 in future if needed.

Turning off the swap is needed when resizing the Linux type partitioning it is just good practice as well as using a live cd as it shows your HD unmounted.

Unallocated would be if you just deleted the sda1 and sda2 partitions leaving a blank space=unallocated ready to be partitioned. 

Now in general with gparted I don't run more then one process at a time. For example if I wanted to delete a partition and put another in I would first delete let it run then run the partition install. I have seen gparted cough up minor sizing problems when you run a few processes together but that is my own experience.

One thing here that has been left out I referenced it, is as open source users we generally say don't do anything until your backed up. So when trying to explain the safest way to do this per standard protocol, the no backup adds a dimension where personally I want to make sure everything goes okay. In other words if you want to really make sure your covered you should have a backup of anything you can't lose, on a external HD.

---

### Post by julio_cortez on 2010-11-05
> **nns2006 said:**
> Below I am attaching my gparted screenshot.
Just a question, out of ignorance (sorry for hijacking but maybe someone can explain this to me as it also happened to me with my current setup).

Where has /dev/sda4 gone in that screen? I would expect something like this to be honest:
```
/dev/sda1 (primary)
/dev/sda2 (primary)
/dev/sda3 (extended)
   /dev/sda4 (logical)
   /dev/sda5 (logical)
   /dev/sda6 (logical)
```..and so on.

Yes, I admit it, I probably have misunderstood something about how partitioning works -_-'

---

### Post by Quackers on 2010-11-05
It may have been deleted at some time in the past.

---

### Post by alaukikyo on 2010-11-05
Just wanted to warn you that if you have selected to automount all ntfs partitions at start(as many sites suggest) deleting the partition will cause troubles so it might be better to format it :)

---

### Post by nns2006 on 2010-11-05
Thank you everyone. I have successfully removed the W7 partition. Everything is alright.:popcorn:

---

