---
title: "Not sure how to install on specific partition despite documentation"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by mcullet on 2008-12-07
Hi all,

Please accept my apologies for this post ... I don't know the right question to ask nor where to look (in the documents).

I have a 500 gig hard drive with 4 partitions (3 x 111 gig and 1 x 131 gig).  I've already installed XP PRO on the first two partitions (drives C & D) and would like to install VISTA Ultimate on the third (drive E).

I'd like to install UBUNTU on the fourth partition (drive F) which has about 131 gig of space - should be plenty of room.  I've formatted it to NTFS thinking it would make it easier to find during the install process (wrong :).

So far as I can tell UBUNTU is happy enough on a variety of different file formats but some are 'better' than others because they offer more improved security features / opportunities.

I don't want to resize any of the Windoze installations ... prefer each goes / stays where they are directed.

(a) How do I make sure UBUNTU installs on the correct partition?
(b) Should I reformat the UBUNTU install partition to any particular file format?  

I've used this as a guide ([http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)) but the author assumes an environment with one partition in which XP is installed.  This seems to follow the UBUNTU install guide which lets me use a 'slider' to modify the size of the XP partition so I can squeeze UBUNTU onto it.

Once again, my apologies for such a basic question.  

Regards,

Mike
Australia

---

### Post by cdmike2k8 on 2008-12-07
I believe there is a choice for manual when you get to partitioning, and from there you can choose/format if needed.

---

### Post by bobnutfield on 2008-12-07
It should be quite easy to install to the correct partition.  If you install from the LiveCD, it will give the opportunity to do manual partitioning (do NOT choose Auto partitioning or it will take your whole drive.)

Ubuntu will recognize the Windows partitions and also recognize their file systems.  It all liklihood, Ubuntu will identify your partitions as sda1, sda2, and sda3 and sda4, with sda4 the partition you wish to install to.  Choose the ext3 file system, and install to that partition and your Windows partitions will not be disturbed.

However, you will need to install Grub to the MBR (the boot sector of the drive).  This will overwrite the Windows MBR, but you will need Grub to give you the choice of OS's to boot from.  It is the norm in Linux and Ubuntu.

There are a number of guides here on the forums for multi-booting.  I do it myself on a number of computers with three or more Linux flavors, all using Grub to boot.

---

### Post by Paqman on 2008-12-07
> **mcullet said:**
> 
(a) How do I make sure UBUNTU installs on the correct partition?
(b) Should I reformat the UBUNTU install partition to any particular file format?  


Both of these can get the same answer: ext3.

Ext3 is a the normal Linux filesystem. If you format the partition to that, you'll easily be able to tell which one you should put Ubuntu on when you run the installer (manual partitioning option) since it will stick out from the other ntfs partitions.

However, there's an issue you may not be aware of: normally Ubuntu is installed onto at least two partitions. The normal minimum is one ext3 partition for the main system, and a small swap partition that works like the Windows pagefile.

The problem with this is that you can normally only have four partitions on one drive. You already have four, so there's no room for your swap. This is bad. However, there is a solution. You can create an extended partition which can have further partitions nested within it. This breaks the four partitions problem.

So in short I would recommend:

Partition 1: WinXP
Partition 2: WinXP
Partition 3: Vista
Partition 4: Extended
(Partition 5: Ubuntu)
(Partition 6: swap)

(5&6 being nested inside 4)

A good tip is to actually create a third partition for Ubuntu and mount the system's /home folder there. This stores all your user data and settings seperately and allows you to reinstall without having to set everything up from scratch.

---

### Post by mcullet on 2008-12-10
> **Paqman said:**
> Both of these can get the same answer: ext3.

Ext3 is a the normal Linux filesystem. If you format the partition to that, you'll easily be able to tell which one you should put Ubuntu on when you run the installer (manual partitioning option) since it will stick out from the other ntfs partitions.

However, there's an issue you may not be aware of: normally Ubuntu is installed onto at least two partitions. The normal minimum is one ext3 partition for the main system, and a small swap partition that works like the Windows pagefile.

The problem with this is that you can normally only have four partitions on one drive. You already have four, so there's no room for your swap. This is bad. However, there is a solution. You can create an extended partition which can have further partitions nested within it. This breaks the four partitions problem.

So in short I would recommend:

Partition 1: WinXP
Partition 2: WinXP
Partition 3: Vista
Partition 4: Extended
(Partition 5: Ubuntu)
(Partition 6: swap)

(5&6 being nested inside 4)

A good tip is to actually create a third partition for Ubuntu and mount the system's /home folder there. This stores all your user data and settings seperately and allows you to reinstall without having to set everything up from scratch.

Hi all,

Thanks HEAPS for the prompt and very helpful responses.  And please accept my apologies for not having responded sooner ... Windoze installation hassles have been rather interesting to resolve and I've not been able to get a stable system long enough to respond.  (Tracked it down to a specific windows update patch but it took time.)  No biggie ...

I can see where you are going with the installation process.  It's no big deal to restructure my drive along the lines that have been suggested - heck, I've reinstalled Windoze so often I can do it with my eyes closed.

Under UBUNTU, my PC feels as if it has been given a heart transplant - I mean ... DAMN!  It just does what I want with minimal fuss and great speed.  

Major smiles this end ... 

Once again, thanks for the excellent help :)

Mike
Australia

---

