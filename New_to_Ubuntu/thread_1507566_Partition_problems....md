---
title: "Partition problems..."
date: 2010-06-11
forum: New to Ubuntu
---

### Post by johnnyflips on 2010-06-11
Hi everyone. I am what you call a newbie, I guess anyone who has trouble getting it installed already has that label , huh? Anyway, I have two hdds. One is particularly small and contains windows. The other is 160g and I only use it for storage, of which 40g are taken. I want to install Ubuntu on the larger drive but it is formatted for windows and the setup program only gives me the option of splitting the windows partition, but I want to split the other one, and I don't have anywhere to store the other information to do a clean install. Is there some way to compact the information into a smaller partition and create a partition for Ubuntu. Please help,

---

### Post by oldfred on 2010-06-11
Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
Dual Boot win/10.04
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

I prefer to use gparted from the liveCD or download a separate gparted liveCD. Others may say Parted Magic is better.

If you set up partitions in advance you then can also include a separate /home. The auto installs just give you root (/) and swap.

I recommend root of 10-20GB when you have /home separate and swap of 2GB or RAM size if you want to hibernate and the rest as /home. You can label but do not use during partitioning.

You then have to use manual install and specify the partitions you created. On the last partition screen you need to use the advanced button if you have more than one drive. You want grub installed to the MBR of the same drive you install to. Then in BIOS set that drive as the boot drive.
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

---

### Post by sandyd on 2010-06-11
> **johnnyflips said:**
> Hi everyone. I am what you call a newbie, I guess anyone who has trouble getting it installed already has that label , huh? Anyway, I have two hdds. One is particularly small and contains windows. The other is 160g and I only use it for storage, of which 40g are taken. I want to install Ubuntu on the larger drive but it is formatted for windows and the setup program only gives me the option of splitting the windows partition, but I want to split the other one, and I don't have anywhere to store the other information to do a clean install. Is there some way to compact the information into a smaller partition and create a partition for Ubuntu. Please help,
System -> Administration -> Gparted
select the drive (top right)
right click on the partition and resize it (note that resizing it by creating free space AFTER the partition is occasionally faster than creating it BEFORE).
Now go back to the ubuntu installer and at the partitioning stage, select "use largest block of free space"

oh, and don't do that if your using windows 7

---

### Post by Mark Phelps on 2010-06-11
Having done dual-booting for years, let me share some advice ...

Since you have separate drives, disconnect the MS Windows drive when you install Ubuntu.  This will prevent the problem of overwriting the MS Windows MBR with GRUB.

Once you have Ubuntu installed, reconnect the MS Windows drive, but continue to boot from the UBuntu drive.

Then, open a terminal in Ubuntu and enter "sudo update-grub".  This should auto-generate a new GRUB config file that will include an entry for booting MS Windows as well as Ubuntu.

---

### Post by johnnyflips on 2010-06-12
Thank you very much everyone. I compressed and repartitioned my hdd. Then as suggested I unhooked my "windows" drive and installed Ubuntu, shut down, plugged c: back in and windows loaded up. I tried unplugging c: and starting but got "no operating system. How do I plug in the c: drive and still load into Ubuntu? I feel stupid to not figure it out, but common sence told me to reboot with cd but it loaded into a live session and not the version on my hdd. Thanks for all your help

---

### Post by oldfred on 2010-06-12
You should be able to choose which drive to boot from in BIOS. Unless you have older IDE drives with master & slave settings.

---

### Post by varunendra on 2010-06-12
> **oldfred said:**
> You should be able to choose which drive to boot from in BIOS. Unless you have older IDE drives with master & slave settings.
Correct!
Putting Ubuntu drive "BEFORE" the Windows drive in the "Boot Order" in BIOS is the simplest way. If any of your drives is SATA, then I assume your BIOS must be modern enough to provide the option to choose between the two drives- which one should boot first.

Just in case you have only IDE drives and such an old BIOS that doesn't provide the above option, then simply reset the jumper settings (on the backs of the hard-disks) to make Ubuntu drive "Master" & the Windows one "Slave", & connect them through same IDE cable.

---

### Post by SRST Technologies on 2010-06-12
> **Mark Phelps said:**
> Having done dual-booting for years, let me share some advice ...

Since you have separate drives, disconnect the MS Windows drive when you install Ubuntu.  This will prevent the problem of overwriting the MS Windows MBR with GRUB.

Once you have Ubuntu installed, reconnect the MS Windows drive, but continue to boot from the UBuntu drive.

Then, open a terminal in Ubuntu and enter "sudo update-grub".  This should auto-generate a new GRUB config file that will include an entry for booting MS Windows as well as Ubuntu.
This is a horrible way of doing it.  First, when you disconnect the drive, you're taking the ability for GRUB to be written to the MBR (and there's only one that matters on any computer) which is pointless considering what you said to do later in the tutorial.

How are they to continue to boot from the Ubuntu drive when they reconnect the MS drive?  You didn't tell them how to prevent Windows (which will be the first drive and thus the only MBR considered by the computer) from booting and how to use Ubuntu when he/she does this.

If you want them to update grub after magically stopping Windows and starting Ubuntu even though you didn't tell them how to do it, it's either going to complain that GRUB is not in the MBR, because the MBR that the OS will look at is the first hard drive, and that's going to have Windows on it.  Or, it'll just write GRUB to the MBR of the Windows drive, which defeats the purpose of disconnecting the drive to preserve ntldr.

Don't do it.  Just install Ubuntu on the second drive, and let it write the new boot sector, and it will automatically discover Windows when you install and let you pick it right from the beginning without having to open your case or muck about with disconnecting and reconnecting drives.

---

### Post by johnnyflips on 2010-06-12
Ok, I had to reinstall windows and now have windows on one drive, and Ubuntu on another, along with some windows storage. I ran Ubuntu as a live cd and sudo apt-install grub. It said it installed it but I still boot into windows. Should I change the order of my hdds now so that it tries to boot Ubuntu first, or just reinstall Ubuntu and let it do it's thing? With the windows drive hooked up this time. Thanks for all your help, I really appreciate it!!

---

### Post by oldfred on 2010-06-12
Do not physically change drives but in BIOS switch to boot the other drive.

If you have to rediscover windows 

sudo update-grub

I always prefer not to disconnect drives but then you have to be very careful to use the advanced button to make sure where grub is installing itself. Of course you can easily reinstall grub or windows boot loaders if you do make a mistake.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by johnnyflips on 2010-06-12
I tried changing the bios and it comes up file system not recognized and goes into a grub recovery prompt. The storage on that drive is first on the drive, is that maybe why it doesn't pick up the Ubuntu? I really don't want to do anything that could compromise that information. Is it a problem that they're not on the same drive?

---

### Post by -kg- on 2010-06-12
> **carlee said:**
> System -> Administration -> Gparted
select the drive (top right)
right click on the partition and resize it (note that resizing it by creating free space AFTER the partition is occasionally faster than creating it BEFORE).
Now go back to the ubuntu installer and at the partitioning stage, select "use largest block of free space"

***PLUS - ONE!!***  That is absolutely the easiest way to do it, in your circumstances, unless you want to create a separate /home or other partition(s) (I'm starting to become ambivalent about their necessity or desirability these days).  If you want the extra partitions, you would need to choose the manual partitioning option and create them yourself (or mark the mount points of the partitions you already have/have created).

In this manner, you could install to the free space on the secondary hard drive while installing GRUB in the MBR of the primary hard drive, to multi-boot both OSes.  It's the easiest way to do it, and you won't have to switch hard drives in order to boot between them.

> **carlee said:**
> oh, and don't do that if your using windows 7

Considering that we're shrinking a second partition and not the partition in which Win7/Vista is installed, I don't think that would actually be a problem, but to be safe I would use the Windows Partition Manager for that operation, anyway.  It won't hurt anything and will accomplish the same thing.  But...

> Thank you very much everyone. I compressed and repartitioned my hdd.

Considering the operation is already complete, the point is moot.

---

