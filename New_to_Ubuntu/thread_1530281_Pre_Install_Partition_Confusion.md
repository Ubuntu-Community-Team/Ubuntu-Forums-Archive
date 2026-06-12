---
title: "Pre Install Partition Confusion"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by oschoices on 2010-07-13
Hi All,

Newbie to Ubuntu but been computing with Windows for many years and finally thought that I should give Ubuntu a try.

I am using quite an old PC that I built about a decade ago and I have not touched much on partitions.  I read the Dual Boot Partitions article in the Community Documentation section but found the example a bit confusing with some of the referrences such as sda1, sda2, ext3, ext4 etc.  

[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)

I was thinking of doing an XP reinstall anyway so am happy that can be done first and the ubuntu install afterwards.

As I mentioned my PC is a bit old but I have used the Ubuntu 10.04 Desktop Edition to boot from the CD Rom and that ran ok.  I'm assuming some of my hardware is only using generic drivers at this stage but that some of these could be replaced if available from hardware manufactures once I've installed.

I have learnt the hard way with Windows to prepare for the worst and use a drive image creation program (Acronis True Image Home) which can create a recovery partition.   Will Windows see all of the partitions on the drive after Ubuntu has been installed and would it be possible to create a drive image of specific partitions so that the OS ones can easily be restored?  Will Ubuntu leave the boot option to boot into the Acronis recovery manager intact?

A little about my PC...
Dual Pentium III 500Mhz processors, think these also have 1MB L2 cache on each, 1GB RAM, SCSI hard drives have now been replaced with a single SATA 500GB Samsung F3 in JBOD config using a PCI SATA RAID card by HighPoint, SCSI DVD/CD ROM not bootable due to conflict between SCSI and SATA controllers, therefore using a SATA to IDE converter with a new SATA DVD Combo drive which is bootable.

Judging by the Partitions article above (i.e. sda1 through to sda7) I think that would suite my case but it mentions if RAM is less than 1GB the author Tom would do things very differently and as my system is 1GB I wonder what the best partition scheme would be?

Lets say I start with a reformatted 500GB drive, I usually run gdisk to do a good wipe first, then boot from the Windows XP install disc to let that install onto a single primary partition, I think.  Install Acronis in Windows which sets up the recovery partition.  How do I shrink the Windows partition within Windows though?

Would I then bootup from the Ubuntu CD so that I can use GParEd to create the additional partitions?

From the example partitioning scheme, is the sda3 Primary Partition an additional Primary Partition to the one Windows is on?  Is sda3 the partition that Ubuntu is going to install to?

**sda1** Recovery Partition, around 10-15GB depending on how many image versions to store here and whether Acronis can also create an image of the Ubuntu partition, one quite minimal Windows image is 3GB.

**sda2** Windows Partition, 30GB 
**sda3 **Primary Partition, 10GB big enough for Ubuntu plus apps?
**sda4** Extended Partition, remainder of drive, aprox. 410GB*
[INDENT]**sda5** Logical Partition, bulk of remainder of drive, i.e. 398GB, definately to share with Windows.

**sda6** Logical Partition, same size as sda3, test area for trying new distros.

**sda7** Logical Partition, 2GB? swap file, any advantage to making this larger?

[/INDENT]*Although I referred to my drive being 500GB it reports as 465GB in Windows.

Would it be better to share out some of the space from sda5 to other partitions as I don't want to run out of space on the OS partitions and later I am thinking of storing user files on a network drive?

I'm also confused over the mention of creating a separate /boot partition, would this really be necessary if I can create partition images as I would hope to restore sda3? from the image that I would have tweaked to my liking?

Sorry this has grown into quite a long 1st post...

Any feedback much appreciated.

---

### Post by bodhi.zazen on 2010-07-13
Partitions are physical divisions of your hard drive , see

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

Within a partition you format it with a file system. Windows uses FAT (linux calls this vfat) or NTFS.

Linux file systems include ext2 , ext3, and the default is now ext4. There are many other options including xfs, jfs, btrfs, etc.

You should probably stay with the defaults.

For additional information see:

    [http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)
    [http://www.linux.com/articles/31966](http://www.linux.com/articles/31966)

In terms of installing, I suggest you star with the defaults. This is two partitions, 

/ or "root" and a swap partition. Your swap partition should be RAM X 2 , max 1 Gb.

If you , you may make a data partition or a separate home partition. The advantages of this is that you keep your user data separate from the OS , and you can easily re-install without losing your data (user data is kept in /home).

You do not need a separate /boot or /var or /usr at this time.

[img]http://hyders.com/wp-content/uploads/2009/09/filesystemhierarchyhb8.jpg[/img]

---

### Post by YesWeCan on 2010-07-13
Hi.
I was an experienced Windows user and migrated to Ubuntu a year ago. I now run Ubuntu and XP. Ubuntu has freed me from the shackles of Windows and has transformed and reinvigorated my whole computing experience. I hardly ever use XP now.

My advice to "me a year ago" would be:
1) Install XP on its own disk. For the cost of a small disk these days it is not worth the potential agonizing hassle of having dual booting on the same disk. Windows is not a good bedfellow with other OS. Problems arise when you update it and it wipes the Ubuntu boot-loader. Vista is known to crash during updates when a grub boot-loader is detected. Not sure about Win7.
2) Do not use hardware RAID systems. If you want RAID then create a software RAID volume on your Ubuntu disk.

Now, if you are experienced enough you can make anything you like work. I am just saying that if I were advising my novice self I would start with XP on its own disk. Install Ubuntu and grub on a separate disk and boot off this disk; you can then choose to boot XP from the grub menu. Mixing it all up when you are a novice is asking for hours of troubleshooting.

I have a disk dedicated to XP. I have a disk dedicated to Ubuntu 10.04. I have two disks formatted in ext4 as a RAID 1 array. I deliberately keep XP in its own containment zone!

Be aware that Ubuntu can mount Windows filesystems but Windows cannot (will not ;-)) mount linux filesystems. So you can use Ubuntu to backup your Windows files, for instance.

Brian

---

### Post by oschoices on 2010-07-14
Thank you both very much for your time and responses, I think once I have made sure I have everything I need for my XP reinstall I shall give things a try.  Am just going to use the one hard drive for the time being and see how I get on.

---

### Post by oschoices on 2010-07-23
Hi all,

I am sort of up and running, the extra partition for Windows recovery complicated things a bit as it needed to be done using Acronis which created an extended partition and logical drive.  Doing this before setting up additional partitions for Ubuntu meant that the Ubuntu install would only create more logical drives in the extended partition rather than allowing the creation of further primary partitions.  

I got round this by using Acronis to remove the recovery partition.  This got me back to having just one partition with XP installed on it and the remainder of the drive as unallocated space.  I then chose to use the Ubuntu CD and GParted to create the remainder of the primary partitions and an extended partition.  At this point I booted back into XP and recreated the Acronis recovery partition so this time it would be the next sequential number i.e. sda5.  Then I went back to GParted in Ubuntu to create some additional logical drives in the extended partition. 

So this is how my drive looks at the moment;

/dev/sda1 ntfs 50GB Windows Flags=boot
/dev/sda2 ext4 10GB Ubuntu  Mount=/
/dev/sda3 ext4 10GB not currently in use
/dev/sda4 extended partition 371GB
  /dev/sda5 fat32 Acronis Secure Zone / Recovery Partition 10GB
  /dev/sda6 ntfs 350GB Mount=/data
  /dev/sda7 ext4 100MB Mount=/boot
  /dev/sda8 ext4 10GB not currently in use
  /dev/sda9 linux-swap 1GB
  unallocated space 24GB

Part of setting up the Acronis Secure Zone is to enable a boot loader that allows booting directly into the recovery manager to enable the re-imaging of the Windows partition.  Before enabling this, Acronis has a dialog that says "For Linux loaders (e.g. LiLo and GRUB) you might consider installing them to a Linux root (or boot) partition boot record instead of MBR before activating the Acronis Startup Recovery Manager".

On my first Ubuntu install attempt when I got to the stage just before the install would start there was an Advanced button which related to the boot loader and where this should go.  This was defaulted to sda but as I had a boot partition (sda7) I chose this, thinking that was what Acronis was referring to.  Unfortunately this did not bring up the Grub menu when rebooting on completition of the install.  I then thought perhaps the boot flag should be moved to sda7 but this still didn't work and gave an error on reboot of MBR error 1.

I then cleared down my 1st install attempt using the Live CD, moved the boot flag back to sda1 and formatted the Ubuntu partitions.  

2nd attempt same as 1st but this time I left the default on the boot loader to go to sda but won't this get overwritten or messed up when I enable the Acronis Boot Loader?

Having now allowed the Ubuntu Update Manager to bring things up to date I also now have 2 versions of Ubuntu in the Grub menu;

Ubuntu, with Linux 2.6.32-23-generic
Ubuntu, with Linux 2.6.32-23-generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Microsoft Windows XP Professional (on /dev/sda1)

Does this mean I have two whole versions bloating my drive out due to an update or is it just using some parameters to be able to offer both the old and the new.  I can see why it might be an idea to have both in case of problems but eventually I would prefer just to have the most up to date version.  Is that just a case of somehow removing unwanted entries from the Grub menu?

Any more help please...

---

### Post by bodhi.zazen on 2010-07-23
I do not know the answer to yoru questions on Acronis as I am not familiar with it.

If you are new to Ubuntu is is almost always best to go with the defaults when installing. The defaults work well and, IMO, all too often I see new users trying to change the default settings without understanding what they are doing -> usually causes more problems.

In terms of the multiple listings, those are kernels. As with other applications the kernel is updated from time to time and higher numbers = most recent kernel.

Ubuntu keeps the old kernels. If the new kernel does not boot, try the old one.

See also :

[http://ubuntuforums.org/showthread.php?t=844059](http://ubuntuforums.org/showthread.php?t=844059)

[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

---

