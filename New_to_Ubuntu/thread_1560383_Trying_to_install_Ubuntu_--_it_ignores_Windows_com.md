---
title: "Trying to install Ubuntu -- it ignores Windows completely and reports the whole HDD"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by Hork on 2010-08-24
as blank.

Is it possible to fix this? It thinks everything is "free space" and there's no other operating system on it.

I really want to install Ubuntu for programming. :(

---

### Post by skatinjj on 2010-08-24
> **Hork said:**
> as blank.

Is it possible to fix this? It thinks everything is "free space" and there's no other operating system on it.

I really want to install Ubuntu for programming. :(

What are you using to view the hard drive?

---

### Post by Hork on 2010-08-24
> **skatinjj said:**
> What are you using to view the hard drive?

I am using "Install Ubuntu 10.04 LTS". It detects the hard drive, just it detects everything as free space.

---

### Post by skatinjj on 2010-08-24
> **Hork said:**
> I am using "Install Ubuntu 10.04 LTS". It detects the hard drive, just it detects everything as free space.

And you can boot into windows and use it just fine?

Could you post a screen shot?

---

### Post by Hork on 2010-08-24
> **skatinjj said:**
> And you can boot into windows and use it just fine?

Could you post a screen shot?

Of Ubuntu or Windows? or both?

---

### Post by skatinjj on 2010-08-24
> **Hork said:**
> Of Ubuntu or Windows? or both?

Of the partition screen during the Ubuntu install where you select how to partition the drive.

---

### Post by Hork on 2010-08-24
> **skatinjj said:**
> Of the partition screen during the Ubuntu install where you select how to partition the drive.

Here is Windows, booting into the Ubuntu installation to take a screenshot

---

### Post by LiquidMeson on 2010-08-24
is 10.04 on a usb? did you try booting the cd without the removable drive?

---

### Post by vlamnire on 2010-08-24
Did you select the option similar to install side by side?

---

### Post by Hork on 2010-08-24
> **vlamnire said:**
> Did you select the option similar to install side by side?
It happens before I even make a choice and after. See the attached pictures. I don't want to go beyond these steps because I don't want to format my HDD.

What could the issue be?

---

### Post by Hork on 2010-08-24
> **LiquidMeson said:**
> is 10.04 on a usb? did you try booting the cd without the removable drive?

Yes. No.

Not even Wubi works. :(

---

### Post by wilee-nilee on 2010-08-24
Windows 7 needs to be shrunk with its disc manager leaving a open space. The disc manager in W7 is a virtual partitioner that will tell you how small you can make the main partition. 

Do not do a side by side install; shrink the partition with windows then install in the open space, after rebooting windows to make sure everything is working..

---

### Post by Hork on 2010-08-24
> **wilee-nilee said:**
> Windows 7 needs to be shrunk with its disc manager leaving a open space. The disc manager in W7 is a virtual partitioner that will tell you how small you can make the main partition. 

Do not do a side by side install; shrink the partition with windows then install in the open space, after rebooting windows to make sure everything is working..

Shouldn't Ubuntu be able to detect the two partitions I have right now though?

---

### Post by skatinjj on 2010-08-24
> **Hork said:**
> It happens before I even make a choice and after. See the attached pictures. I don't want to go beyond these steps because I don't want to format my HDD.

What could the issue be?

Irrelevant, little behind sorry

---

### Post by Hork on 2010-08-24
> **skatinjj said:**
> What is the removable drive showing on the windows disk manager?

Have you tried booting without it?

Works fine on Windows Disk Manager. Doing it without it right now...

---

### Post by Hork on 2010-08-24
> **Hork said:**
> Works fine on Windows Disk Manager. Doing it without it right now...

Same issue. :(

I guess I'm not going to be able to install Ubuntu?

---

### Post by ercferret18 on 2010-08-24
Type "sudo fdisk -l" into a terminal and post the output here.

---

### Post by wilee-nilee on 2010-08-24
> **Hork said:**
> Same issue. :(

I guess I'm not going to be able to install Ubuntu?

I think you will, lets just get more information. Post the boot script in my sig in code tags as described.

---

### Post by Hork on 2010-08-25
> **ercferret18 said:**
> Type "sudo fdisk -l" into a terminal and post the output here.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40bc703f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       91201   732467200    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.




Do I need to do anything else? It sounds like my partitions are messed up.

---

### Post by wilee-nilee on 2010-08-25
I don't think your partitions are a problem. The GUID type partition is the problem. We don't run into this often so it might take a little time to get you some help.

---

### Post by Hork on 2010-08-25
> **wilee-nilee said:**
> I don't think your partitions are a problem. The GUID type partition is the problem. We don't run into this often so it might take a little time to get you some help.

Is it possible to change the partition type?

---

### Post by wilee-nilee on 2010-08-25
> **Hork said:**
> Is it possible to change the partition type?

Here is a link to the wikipedia on this. The wiki wont give you the answers but a overview.
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

I'm not familiar with what to do under this set-up, but there are a few that are so that is where we are at.

---

### Post by ercferret18 on 2010-08-25
Can you see your partitions in GParted? (System > Administration)

---

### Post by srs5694 on 2010-08-25
First, your disk seems to be MBR-partitioned but has leftover GPT data from an earlier partitioning attempt. (Was the disk ever used in a Macintosh? If so, that's where the leftover GPT data comes from.) This *might* be the source of the problem, and it could cause problems down the line. I recommend you use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program to correct the problem:


[list=1]
[*]Boot an emergency recovery disc that includes GPT fdisk, such as System Rescue CD or PartedMagic.
[*]Open a text-mode command prompt and type "gdisk /dev/sda" (or possibly "gdisk /dev/hda"). The program will probably complain that it's found a valid MBR and valid GPT data, and ask which to use. Either will work fine.
[*]Type "x" to enter the experts' menu.
[*]Type "z" to "zap" (destroy) the GPT data.
[*]Type "y" to proceed.
[*]*Type "n" when asked whether to wipe out the MBR.* If you type "y" here, you'll destroy your Windows installation, so be very very careful!
[/list]


You can try again at this point. If it works, then great; however, it's possible that your MBR partitions still have a subtle problem, which might be the true cause of the symptoms you're seeing. This problem is trickier to fix, but it can still be done with a bit of care. See my ["Missing Partitions in GParted"](http://nessus.rodsbooks.com/missing-parts/index.html) page for details.

---

### Post by rickatnight11 on 2011-03-31
> **srs5694 said:**
> First, your disk seems to be MBR-partitioned but has leftover GPT data from an earlier partitioning attempt. (Was the disk ever used in a Macintosh? If so, that's where the leftover GPT data comes from.) This *might* be the source of the problem, and it could cause problems down the line. I recommend you use my [GPT fdisk (gdisk)]("http://www.rodsbooks.com/gdisk/") program to correct the problem:


[LIST=1]
[*]Boot an emergency recovery disc that includes GPT fdisk, such as System Rescue CD or PartedMagic.
[*]Open a text-mode command prompt and type "gdisk /dev/sda" (or possibly "gdisk /dev/hda"). The program will probably complain that it's found a valid MBR and valid GPT data, and ask which to use. Either will work fine.
[*]Type "x" to enter the experts' menu.
[*]Type "z" to "zap" (destroy) the GPT data.
[*]Type "y" to proceed.
[*]*Type "n" when asked whether to wipe out the MBR.* If you type "y" here, you'll destroy your Windows installation, so be very very careful!
[/LIST]


You can try again at this point. If it works, then great; however, it's possible that your MBR partitions still have a subtle problem, which might be the true cause of the symptoms you're seeing. This problem is trickier to fix, but it can still be done with a bit of care. See my ["Missing Partitions in GParted"]("http://nessus.rodsbooks.com/missing-parts/index.html") page for details.

This is exactly what I needed.  Thanks so much!

---

### Post by missionpilot on 2011-07-19
> **srs5694 said:**
> First, your disk seems to be MBR-partitioned but has leftover GPT data from an earlier partitioning attempt. (Was the disk ever used in a Macintosh? If so, that's where the leftover GPT data comes from.) This *might* be the source of the problem, and it could cause problems down the line. I recommend you use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program to correct the problem:


[list=1]
[*]Boot an emergency recovery disc that includes GPT fdisk, such as System Rescue CD or PartedMagic.
[*]Open a text-mode command prompt and type "gdisk /dev/sda" (or possibly "gdisk /dev/hda"). The program will probably complain that it's found a valid MBR and valid GPT data, and ask which to use. Either will work fine.
[*]Type "x" to enter the experts' menu.
[*]Type "z" to "zap" (destroy) the GPT data.
[*]Type "y" to proceed.
[*]*Type "n" when asked whether to wipe out the MBR.* If you type "y" here, you'll destroy your Windows installation, so be very very careful!
[/list]


You can try again at this point. If it works, then great; however, it's possible that your MBR partitions still have a subtle problem, which might be the true cause of the symptoms you're seeing. This problem is trickier to fix, but it can still be done with a bit of care. See my ["Missing Partitions in GParted"](http://nessus.rodsbooks.com/missing-parts/index.html) page for details.

This just fixed my problem as well. Thank you so much!

---

### Post by srs5694 on 2011-07-19
FWIW, the problem of extraneous GPT data can now be fixed a bit more easily and more safely (with fewer chances of messing it up) with my [FixParts](http://www.rodsbooks.com/fixparts/) program. This program shares a lot of code with gdisk, but FixParts is designed to fix this and a few other MBR partitioning problems, whereas gdisk is really an fdisk workalike for GPT disks.

---

