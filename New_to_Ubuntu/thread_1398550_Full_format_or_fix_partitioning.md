---
title: "Full format or fix partitioning?"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Alex De Duck on 2010-02-04
Hi, I've run into a spot of trouble. I was partitioning my hard drive, and made sure everything was good for vista - the part I left for it was large enough, and I made sure it was ntfs. Vista, however, refuses to be installed on it. Only error I found was that the partition was primary, not logical. A run of the command "Free" gave me this: 

             total       used       free     shared    buffers     cached
Mem:       3087308    1512284    1575024          0     269808     794040
-/+ buffers/cache:     448436    2638872
Swap:      6385796          0    6385796

---

### Post by audiomick on 2010-02-04
I think Vista actually has to go in a primary partition.

Post the output of
```
sudo fdisk -l
```
so we can see what you have got for partitions.

---

### Post by Alex De Duck on 2010-02-04
Here goes: 

```

	 	 	 	 	  Disk /dev/sda: 160.0 GB, 160041885696 bytes 
 255 heads, 63 sectors/track, 19457 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0xf8000000 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1       18662   149902483+  83  Linux 
 /dev/sda2           18663       19457     6385837+   5  Extended 
 /dev/sda5           18663       19457     6385806   82  Linux swap / Solaris 
  
 Disk /dev/sdb: 250.1 GB, 250059350016 bytes 
 255 heads, 63 sectors/track, 30401 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0x52773fc0 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1   *           1       20590   165389143+   7  HPFS/NTFS 
 /dev/sdb2           20591       30401    78806857+   5  Extended 
 /dev/sdb5           20591       29996    75553663+  83  Linux 
 /dev/sdb6           29997       30401     3253131   82  Linux swap / Solaris 


```

---

### Post by audiomick on 2010-02-04
It looks like you already have two Linux systems on there. Is that right?

As far as the partitioning goes, it actually looks ok. sdb1 is 165GB or thereabouts, if I am reading that right. It is a primary and the first on the drive. As far as I know, Vista should be happy with that. I am not an expert though. It would be wise to wait for a second opinion before you do anything radical.

About the only thing that occurs to is to try changing the boot order, or even unplug the other drive completely for the duration of the install. Both of those options run the danger of messing up your grub, but a windows install will do that anyway.

---

### Post by Alex De Duck on 2010-02-04
Yes, I have mint installed too, but I'm thinking of throwing that one off as I've been trying to have it work with my wifi for the last two days... Uncompatibility thy name be Broadcom. 

I have a part of about 70 gb reserved for Vista, which I figured was more than enough. Right now, I'm hoping to find a way to do a clean sweep, forget the partitions, get vista on and then install ubuntu into it using wubi. 

I have an external hard drive - I unplugged it during the installation though, and it has not made a difference so far if it is plugged or unplugged. The rest of the memory is quite fixed in the laptop. 

How is boot order shifted?

---

### Post by audiomick on 2010-02-04
The boot order of the drives is a BIOS setting. It is generally easy to find and easy to understand.

If you have decided to do a "clean sweep", try just deleting all the partitions on the drive and see what Vista does with that.

---

### Post by Alex De Duck on 2010-02-04
How do I do that? The vista disc won't let me delete any partitions. 

I'm a total newb in deleting partitions... I made them with the start up disc for mint.

---

### Post by audiomick on 2010-02-04
Use whatever you used to do the changes. If it was on the mint CD, it was probably gparted, but it doesn't matter much. If it can create partitions, it can delete them. Usually it is just a case of select the partition, then maybe right click or maybe choose out of a menu the option "delete partition".
This will of course delete all data on the partition; if you delete them all, the drive will be empty.

---

### Post by almufadado on 2010-02-04
Download gParted live cd (bootable) from  and burn it.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Unplug all external disks (can plug them later if you want to manage it)

Boot the system with it.

!!!! Check all partitions for errors !!!

Arrange the partitions as you like provided that :

- Max 4 primary/extended partitions per disk -> Extended partitions  are limited by size)

Reboot .

Download, burn and boot with  super grub disk (bootable) to fix the bootloader

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

