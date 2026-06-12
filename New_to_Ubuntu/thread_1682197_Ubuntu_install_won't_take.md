---
title: "Ubuntu install won't take"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by patanellak on 2011-02-05
I had a IRQL_driver crash on my desktop that had Vista OS...after house of frustration decided to install Linux Ubuntu. When trying to boot from Vista I got the BSOD screen no matter what mode I start in. I burned Ubuntu onto a disk from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download), and put the disk into the desktop. I tried Ubuntu for awhile to extract the data from Vista (Pro Tools files). Once I got the data I hit the option on the Ubuntu desktop to install Ubuntu 10.04 LTE. 

Once I get the installation box the system detected Vista. The first time I tried this install I selected a side to side boot (assuming that meant dual boot). The install seemed to go fine and no errors were displayed. Once completed I was prompted to restart the computer and the disk was ejected (was done automatically). I removed the disk, restarted the computer, and the computer gave me a response with an all black screen and white text that I needed to insert a boot disk, as if the machine is not detecting the operating system. 

I put the disk back in and went through the entire install process again but this time I used the options to wipe Vista and to install over Vista. However I am on my 4th attempt in installing Ubuntu and it keeps doing the same thing...all it states is that I need to enter a disk to boot or to reboot with an OS. 

My intention is to have a full install of Ubuntu...I don't want to keep Vista as it is bad anyways. Here are the specs of the desktop:


Technical details-Acer ASpire AX1700-U3700A
•    - 2.4GHz Intel Pentium Dual-Core E2220
•    - 4GB (2x2GB) RAM
•    - 640GB 7200rpm SATA Hard Disk
•    - SuperMulti DVD Burner
•    - nVIDIA GeForce G100 Graphics

What am I doing wrong or am I missing something?

---

### Post by wojox on 2011-02-05
When it gets towards the end and asks if you want to install grub to the Master Boot Record, let it.

---

### Post by Rubi1200 on 2011-02-05
Hi and welcome to the forums :-)

Did you check the integrity of the ISO image?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You also have an option on the LiveCD to check disk for defects, I would try that and see if there is an issue.

Where are the SATA controllers inserted (which ports)?

---

### Post by patanellak on 2011-02-05
Wojox: I restarted the machine since it froze after hitting shutdown within Ubuntu. I pulled the disk out and someone just put in a Vista Upgrade disk (they were curious if that would give back Vista, ugh) Now I have a screen that gives me 8 options such as"

Ubuntu, with Linux 2.6.32-28-generic pae
Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Ubuntu, with Linux 2.6.32-28-generic-pae (on /dev/sda1)
Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode) (on/dev/sda->
Ubuntu, with Linux 2.6.32-28-generic-pae (on/dev/sda6)
Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode) (on/dev/sda->

What should I select?

@Rubi1200: I will do that now on my laptop while I wait for the response in regard to the above aforementioned.

Thanks!

---

### Post by patanellak on 2011-02-05
Rubi1200: I hate to sound so untechie but I don't know how to find the answer to your question: 
"Where are the SATA controllers inserted (which ports)"?-If you don't mind how do I find that answer?

---

### Post by Hedgehog1 on 2011-02-05
> **patanellak said:**
> 

Ubuntu, with Linux 2.6.32-28-generic pae
Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Ubuntu, with Linux 2.6.32-28-generic-pae (on /dev/sda1)
Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode) (on/dev/sda->
Ubuntu, with Linux 2.6.32-28-generic-pae (on/dev/sda6)
Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode) (on/dev/sda->

Thanks!

patanellak,

Your repeated Ubuntu 'side by side' installs have created a number of unwanted partitions on your hard disk.  This is why your GRUB menu is has all these options (and has left you with very little usable disk space).

Your Vista data is long gone after these repeated install attempts; so your best plan of attack is to do a full re-install of Ubuntu that uses your whole disk (and in the process cleans up all the little partitions you have created).

This will give you an Ubuntu only computer...

---

### Post by Rubi1200 on 2011-02-05
Before we get to that, let's deal with some other things.

You appear to have inadvertently installed Ubuntu multiple times (from what you posted above).

As the computer starts, try holding down Shift and see if the GRUB menu comes up with those entries.

If it does, try booting into one of them and see what happens. I would start with the first one.

Second, are you able to boot the computer with the LiveCD?

If yes, choose to try Ubuntu without changes.

At the live desktop, go to Applications > Accessories > Terminal and post the output of the following command:

```
sudo fdisk -lu
```

---

### Post by techunit on 2011-02-05
> **Hedgehog1 said:**
> patanellak,

Your repeated Ubuntu 'side by side' installs have created a number of unwanted partitions on your hard disk.  This is why your GRUB menu is has all these options (and has left you with very little usable disk space).

Your Vista data is long gone after these repeated install attempts; so your best plan of attack is to do a full re-install of Ubuntu that uses your whole disk (and in the process cleans up all the little partitions you have created).

This will give you an Ubuntu only computer...
I am in complete agreement. Do a clean install.

---

### Post by Hedgehog1 on 2011-02-05
Sorry Rubi1200 - didn't realize you were still taking this... I will bow out...  :KS

---

### Post by Rubi1200 on 2011-02-05
> **Hedgehog1 said:**
> Sorry Rubi1200 - didn't realize you were still taking this... I will bow out...  :KS
We posted almost at the same time. There is no need to apologize, we are all here to help in whatever way we can.

I agree with your assessment of the situation :-)

---

### Post by patanellak on 2011-02-05
I did ask you asked and this (and attached ) is the result:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d689d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   317939222   158968587+  83  Linux
/dev/sda2       317939710  1250263039   466161665    5  Extended
/dev/sda5      1233641472  1250263039     8310784   82  Linux swap / Solaris
/dev/sda6       626354176  1217015807   295330816   83  Linux
/dev/sda7      1217017856  1233631231     8306688   82  Linux swap / Solaris
/dev/sda8       317939712   613750783   147905536   83  Linux
/dev/sda9       613752832   626341887     6294528   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
_____________________________________________________________________________________

The issue is that I did a full install the Live Install that was created from the Ubuntu website. I get the same issue. I do see that there are multiple data drives now listed on my desktop (see attached), so I am guessing you are right about the partitioning. I am going to try this once more and see what result I get.[ATTACH]182773[/ATTACH]

---

### Post by patanellak on 2011-02-05
I did try and select each item on the Grub menu, however, once select the screen goes black and nothing occurs; then I have to restart and try the next item with the same result. I will be very excited to not ever have to use Vista again. The only reason I would have to is if I can't get Pro Tools to work or within virtualization. :)

---

### Post by patanellak on 2011-02-05
Question, trying to install again and it is asking this:

The installer hsd detected that the following disks have mounter partitions:

/dev/sda

Do you want the installer to try and unmount the partitions on these disks before continuing? If you leave them mounted you will not be able to create, delete, or resize partitions on these disks, but you may be able to install to existing partitions there.

The the previous 3 attempts at installing this I have select yes. Should I select yes on this install?

---

### Post by Rubi1200 on 2011-02-05
I suggest you follow the advice posted by Hedgehog1 and go for a fresh install.

Before you start, check the integrity of the CD and burn again at the lowest possible speed:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

What I would also suggest is when you start the LiveCD go to System > Administration > GParted and if you see any mounted partitions (key symbol next to the partition), unmount them including swap (right-click > Swapoff).

Then, delete ALL partitions leaving the whole drive unallocated. In other words, GParted should show a big gray space and say unallocated for the drive.

Start the installer and choose erase and use entire disk and let it do all the formatting etc.

If you want a separate /home partition for your files, photos etc. ask us how to do that.

If you need more help, please ask.

---

### Post by patanellak on 2011-02-05
Okay, I went through and did as requested. I am going to burn another LiveCD just to be thorough as previously I did not burn at the lowest speed. Then I will complete the rest of the steps.

 One thing I do remember is that I downloaded the 32-bi version of Ubuntu but I think this computer is 64-bit. Though on the d/l page it states 32-bit is recommended should I install the 64-bit anyways?

---

### Post by patanellak on 2011-02-05
Okay, I did all that was asked. The result was a screen (after install and restarting) that states the following:

Reboot and Select proper Boot device
or Insert Boot Media in selected boot device and press a key

Thoughts?

---

### Post by hansolo4949 on 2011-02-05
It sounds like the mbr of your hdd is messed up. If you git your files off of Vista, just set The Ubuntu install to use the entire HDD. If you haven't gotten the data, just boot from a livecd and mount the partition from it, then transfer the files onto some storage media, such as a flash drive. If Ubuntu can recognize the partition, you should be good to go!

---

### Post by patanellak on 2011-02-05
I already saved the data I needed yesterday. After doing all that is instructed above I am getting the same issue, where it says I need to boot from disk. I wiped Vista off and there is nothing partitioned on the drives (as I did was instructed in the above aforementioned). I am concerned since now removing Vista and Linux won't work without a disk, this computer will only be good to use on the internet. Any ideas of what I may be doing wrong or something that may be wrong with the computer?

---

### Post by patanellak on 2011-02-05
I did try checking the integrity of the CD. When you plus in the LiveCD from the burn, a screen is displayed giving you the option to check the cd. I selected that option and hit enter. The screen went blank and nothing happened. So, when I restarted the desktop it didn't give me the same menu, just asked in a GUI type of screen if I wanted to try Ubuntu or if I wanted to install it. So I selected install again.

AS it installed I recall that previous to using the CD, I changed the Boot settings within Bios to boot from cd drive. I was thinking that if I did that, and never changed it back, could this be the cause of the computer not loading the obviously installed Ubuntu without a CD. Thoughts? Should I shutdown and change the boot sequence back to previous settings?

---

### Post by Rubi1200 on 2011-02-06
When Vista was installed did you use any software like Dell DataSafe, Adobe, McAfee or anything else that writes to the MBR?

To the best of your knowledge, was this drive ever part of a RAID array?

You could try changing the settings in BIOS to see if that makes a difference, though I suspect that is not the issue here.

---

### Post by wojox on 2011-02-06
Yes try changing the boot option in bios. Also make sure their is no CD in the drive when you reboot.

As a last ditch effort boot the Live-CD again and erase the MBR and try again:

```
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```

---

### Post by patanellak on 2011-02-06
@Rubi1200-The only software that I used that you listed was Adobe. I had once used McAfee but deleted it in 2009. I don't think that this dive was ever part of a RAID Array but listed at the bottom of this post is the technical details for the hard drive. I changed the bios and it wouldn't even boot to disk until I changes it back to the previous sequence.

Last night someone gave me the idea to partition the drive myself. So, I deleted the previous partitions as you instructed me previously and went though the install. This time I tried to partition the drive myself through advanced options. No matter what file system I selected I kept getting the response "No Root file system is defined, please correct this from the partitioning menu"
This occurred when I selected FAT/32 and dos as the mount point. I also used FA/32 and /windows as a mount point and got the same response. 

So I then tried all of these options and I got the same response:

ext4 journaling  file system, ext3 journaling file system, ext2 file system, ReiserFS  journaling file system, JFS journaling file system, XFS journaling file  system, FAT16 file system, FAT32 file system, swap area, do not use  partition.

Nothing worked. Thoughts?

---

### Post by Rubi1200 on 2011-02-06
This is starting to sound very odd indeed.

When manual partitioning you need to set the mount points, which is why it told you that no root file system is defined. 

In other words, once you create a partition, right-click > change > and then set as /, home, swap or whatever you need it to be.

However, if you have done all this and it is still not working then try the suggestion posted above by wojox to overwrite the MBR.

After running that command, try partitioning and installing again.

EDIT: after running the command given by wojox, use GParted on the LiveCD > Device > Create Partition Table and make a new partition table then start partitioning again.

---

### Post by techunit on 2011-02-07
Why wasn't the clean install working? By using the defaults he should have been able to solve his problem.

---

