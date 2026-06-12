---
title: "Partitioning help to dual boot Lucid 10.04 and Windows XP"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by VinoFuriaRoja on 2010-06-27
Hey there everyone,

I need some serious help here with partitioning.  I am very unfamiliar to partitioning, so please bare with me.  I have a 60GB HD that I want to dual boot Ubuntu 10.04 and Windows XP on.  However, I dont know how to set up the partitions properly so that I can dual boot.  Right now the HD is completely blank, so it would be partitioning from the beginning.  

Can you guys make suggestions as to what I should have? 

Ideally, I would like to have the following on the drive:

40GB - Linux
10GB - XP
10GB - drive share (which is another question. Can I set up a partition to be shared between windows and Ubuntu?  Like a "shared" drive that I can see from windows or XP?)

Again, any and all suggestions would help.  Please be specific as you can as to how I should set up each partition with mounts, swaps, etc. 

Thanks again guys.  Anxiously awaiting help here!  

By the way, I have the LiveCD running on the laptop in question, which is how I am able to make this post!

---

### Post by spiky001 on 2010-06-27
hi I would use gparted make the xp partition 1st, then an extended partition for linux 15gig you will need a swap of twice your memory then make home the rest ntfs partition

xp 10
linux 15
swap twice memory
home the rest ntfs

sorry cant put home on ntfs use ext3

---

### Post by spiky001 on 2010-06-27
have a read here sorry
[http://ubuntuforums.org/showthread.php?t=901127](http://ubuntuforums.org/showthread.php?t=901127)

---

### Post by VinoFuriaRoja on 2010-06-27
Ok I understand that I need to have a swap that is about twice my RAM size,  but what should I set up for the xp partition and the ubuntu partition?  And for the shared drive between ubuntu and windows?NTFS for windows and ext4 for ubuntu?  And where do I mount the drives to?  Please help out a noob guys. Detailed directions on how to do this would be greatly appreciated!  I can repay you for your time somehow!

---

### Post by spiky001 on 2010-06-27
how much space for shared partition do you need?

---

### Post by VinoFuriaRoja on 2010-06-27
about 8-10 GB....just enough to have my music on it.  

Side note, I think its cool that I am doing all this correspondence on the laptop that has a blank HD on!  I am doing this via the LIVE CD install disk as I patiently wait on suggestions on how to partition my drives.  

To recap:

60GB HD

35GB - UBUNTU
10GB - XP
15GB to shared drive and swap partition?????anything else?

Please help

---

### Post by spiky001 on 2010-06-27
use gparted make 1st partition 10G ntfs 2nd (shared 15G ntfs) 3rd extened ubuntu35G minus swap swap will make it,s own

xp10G ntfs_______|shared15Gntfs_______|ubuntu33G_________|swap2G_______|

**load windows 1st**

---

### Post by Paqman on 2010-06-27
> **VinoFuriaRoja said:**
> about 8-10 GB....just enough to have my music on it.  


Make sure you have a bit more space than you need. You should never fill a partition more than about 80% full. If you do you'll get a very fragmented filesystem as soon as you start changing any of the contents.

---

### Post by VinoFuriaRoja on 2010-06-27
So I should definitely install windows first before ubuntu?  Couldnt I install ubuntu first, then windows?

---

### Post by VinoFuriaRoja on 2010-06-27
could someone help me out via aim, yahoo messenger, or msn messenger? id like to have "live", real time help

---

### Post by Paqman on 2010-06-27
> **VinoFuriaRoja said:**
> So I should definitely install windows first before ubuntu?  Couldnt I install ubuntu first, then windows?

You CAN install Windows second, but you'd need to [recover the Grub bootloader]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") after Windows wiped it out. It's not as complicated as that page makes it seem at first glance.

---

### Post by VinoFuriaRoja on 2010-06-27
When creating the Ubuntu partition, should it be ext2?ext3? ext4?

---

### Post by wilee-nilee on 2010-06-27
Since you have a blank HH use the custom install of the XP disk just let it format the partition to the size you want.

XP wont install to a ntfs built by gparted at least it never has for me.

For the Ubuntu install use gparted to make a extended partition that is the size of the Ubuntu size and swap combined, put a primary inside it the size you want, with room left for the swap, then use the rest of the open space for the shared partition which I think a installed XP will see hopefully. If XP doesn't see it you can use the XP disk manger to make the share.

When you go to install Ubuntu after the XP install use the custom install and click on the primary don't format it and use the dropdown to give it root=/, accept then click on it again and install.

You can install either OS in what order you want as the MBR is easy to load but If your HD is still empty go XP first.

---

### Post by VinoFuriaRoja on 2010-06-28
I am happy to report that this project is a success!  I formatted the drive initially using the Windows XP setup disc, and then did the normal install.  At first, XP would not recognize my hard drive, so I just went into the BIOS and disabled SATA.  That worked perfectly.  So I did the install normally, and then went and partitioned the drives for Ubuntu and the share drive as recommended.  Next I did the Ubuntu install and voila!  Dual boot with minimal disk space allocated to Windows!  

I realized afterwards though that the XP that I have is bare bones.....literally. No drivers whatsoever for my ethernet and wireless card.  I had to hunt those down and install them manually.  Now I remember why I switched to Linux!  Anyways, thanks to all who helped out. I learned alot about this project today!  

SOLVED!

---

### Post by wilee-nilee on 2010-06-28
> **VinoFuriaRoja said:**
> I am happy to report that this project is a success!  I formatted the drive initially using the Windows XP setup disc, and then did the normal install.  At first, XP would not recognize my hard drive, so I just went into the BIOS and disabled SATA.  That worked perfectly.  So I did the install normally, and then went and partitioned the drives for Ubuntu and the share drive as recommended.  Next I did the Ubuntu install and voila!  Dual boot with minimal disk space allocated to Windows!  

I realized afterwards though that the XP that I have is bare bones.....literally. No drivers whatsoever for my ethernet and wireless card.  I had to hunt those down and install them manually.  Now I remember why I switched to Linux!  Anyways, thanks to all who helped out. I learned alot about this project today!  

SOLVED!

When you do updates for XP choose the custom update and look in the sidebar the drivers for anything else should be listed.

---

### Post by Paqman on 2010-06-28
> **wilee-nilee said:**
> When you do updates for XP choose the custom update and look in the sidebar the drivers for anything else should be listed.

I've always found Windows Updates to be a *highly* unreliable source for hardware drivers. Much b0rkage has ensued, I leave them well alone now.

---

### Post by wilee-nilee on 2010-06-28
> **Paqman said:**
> I've always found Windows Updates to be a *highly* unreliable source for hardware drivers. Much b0rkage has ensued, I leave them well alone now.

I have had the opposite experience, but I have only been using Windows for about 10 months, which I only use to understand it enough to help the dual-booting people. 

I think you have to make sure you upgrade what you have, but making this sort of statement when this OS has the market share of the worlds desktop market is just plain inaccurate to be honest.:p

I am a open source user but come on.

---

### Post by Evanescence on 2010-06-28
Hi,
Here are steps that you can follow to have a successful installation of a dual boot with XP and Ubuntu.

Note: XP MUST be the first one 'cause it's boot-loader is not capable of booting a LINUX partition. GRUB2 provided by your Ubuntu will however be able to boot even an NTFS. So make sure you start with XP.

1. Boot from Xp and delete all partitions to return to a completely free HDD.
2. Create a new partition of 10GB following the XP set-up utilities.
3. install XP in the 10GB and ignore the rest of the 50GB for now.
4. After successful installation of XP, boot now from Ubuntu.
5. Using Gparted (System>Administration>Gparted) access your HDD existing partition table and on the unallocated part (greyed out) create a new partition of 15GB NTFS or FAT32 to be shared by both Ubuntu and XP. Exit Gparted.
6. By now you should be having 35GB of unallocated space. Good
7. Run the Ubuntu installation and when you get to partition layout, choose 'Manual (advanced)' it's pretty easy, don't get intimidated.
8. You will get a preview of your partition table, highlight the unallocated space by right-clicking it and choosing 'new' and choose to create a Linux ext4 (journalising by default) and reduce the 35GB to something like 33GB so that the remaining 2GB can be used for swap. 
9. Flag the ext4 partition with a FORWARD SLASH (/)
10. On the edited partition table, you should now get a small unallocated area of 2GB. Right-click it, and choose new, followed by "Linux Swap"
11. Now you are ready to proceed with the install. Highlight the ext4 and continue with the wizard.

That should be it, so after installation, the first boot should give you 4 options with XP at the very bottom.

---

