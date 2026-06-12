---
title: "Trying to install 10.04 x64 - I don't see the option for &quot;Install them side by side&quot;"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by MaraSkywhiner on 2010-08-25
I'm hoping someone can help me out here.  I'm using an HP tm2t-1100 with the Intel i5 processor.  I'm currently running Windows 7 Home x64, and I'd like to dual-boot with Ubuntu 10.04 x64.

When I try installing Ubuntu, however, I don't see the option to install Ubuntu next to Windows 7.  Ubuntu also reads that I have 3 operating systems on my computer: Win 7 (loader), and two separate Vista (loaders).  (I'll post a screenshot in a few minutes).

This computer has never had Vista (to my knowledge - I got it directly from the factory 2 days ago).  According to Windows, I have 4 partitions (see the attached screenshot).

I'm wondering if my large number of partitions is confusing the installer.  If so, does anyone have any suggestions?  I'd like to keep the recovery partition because this computer doesn't have a built-in optical drive.

Thanks in advance.

---

### Post by MaraSkywhiner on 2010-08-25
Here's my promised installation screenshot.

I'm also wondering if my problems could be related to HP's QuickWeb.  It connects you to the internet without fully booting up the computer (which I tried to eradicate).  Has anyone had any experience installing Linux on an HP with this "feature"?

Thanks again

NB: The only difference in the screenshots is how far I slid the scrollbar showing the disk allotment.

---

### Post by lkjoel on 2010-08-25
Use the Select Partitions Manually option.

---

### Post by MaraSkywhiner on 2010-08-25
What sizes/formats should I use for the new partitions?  I was planning on using 150 GB for Linux.

---

### Post by lkjoel on 2010-08-25
Drag the Ubuntu partition to 20GB.

---

### Post by wilee-nilee on 2010-08-25
You can only have a maximum of 4 primary partitions on a single hard drive, which you have, you wont be able to add another, as it sits.

You have some different options here, as a OEM you have a firmware partition the last one on the right from your MS disc Management screen shot. You also have a recovery partition D.

One of these will have to be removed most likely D after you set up a recovery schema with the built in system or getting the OEM install set. 

Did the computer come with a recovery disc set or DVD?

---

### Post by MaraSkywhiner on 2010-08-25
Unfortunately, I can't drag to change the sizes of the partition.  You can only do that when selecting "install them side by side."

---

### Post by ajgreeny on 2010-08-25
The problem is that you already have 4 partitions on the disk, so you are unable to make any more unless you delete one or more that already exist.

You appear not to be able to delete either the first or second partition on the disk, the first being the boot partition for Win7, I assume, (SYSTEM), and the second being win7 itself, (C), so you are left with the option to delete either of the other two, the recovery partition for windows (D), or the HP Tools partition (E).

I have no knowledge of windows any more, particularly win7, so can not be sure about how practical it may be to delete the recovery partition, as that may be your only backup of win7 should you need to re-install it.  Nor can I say what the HP Tools partition is for, but I suspect that may be the one to delete, but wait for others to answer first before you do so.

If that is what is accepted as the best way forward you will need to:-

1.   In win7 disk management shrink the large win7 (C) partition to make plenty of space for Ubuntu.  How much will depend entirely on how much you will use it, but make it larger rather than smaller.
2.   Using the ubuntu live CD or win7 disk management, delete the chosen partition (HP Tools?)
3.   In the now unallocated space make a new extended partition, and within that partition create a new logical partition for ubuntu operating system, formatted as ext4 and another for swap of somewhere between 2 and 4 GB depending on the memory of your machine.  You could even make a separate third logical partition in the extended one for /home, as ext4, which you would then setup as home at install time.

See [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) if you want to think more about a separate /home partition, though rather than a separate /home, it may be more appropriate to have a shared logical /data partition formatted as ntfs, and then both OSs will be able to use that for all data files, eg docs, photos, videos, music, etc etc.

---

### Post by wilee-nilee on 2010-08-25
I think it is unlikely that the recovery will work after a Ubuntu install.

Personally on my Acer netbook the XP recovery was in the grub menu and worked, but I have never seen anybody else on this forum have this work for them.

I would call the manufacturer and see about getting a regular install DVD that can be activated or the OEM disc set. You can do the on-board copy of the recover in D but personally I would not ever trust that, when there are other more solid ways of recovery.

---

### Post by MaraSkywhiner on 2010-08-25
Problem solved!  I backed up my HP_TOOLS partition then deleted it.  After that, I could create my new partition.

Ubuntu is now installed.  Now, on to tablet configuration...

Thanks to everyone who responded!

---

### Post by lkjoel on 2010-08-25
Do you want to mark it as solved?

---

### Post by MaraSkywhiner on 2010-08-26
> **lkjoel said:**
> Do you want to mark it as solved?

Yes I do, thanks!

---

### Post by lkjoel on 2010-08-27
Click on Thread Tools, and click on Mark this thread as solved

---

