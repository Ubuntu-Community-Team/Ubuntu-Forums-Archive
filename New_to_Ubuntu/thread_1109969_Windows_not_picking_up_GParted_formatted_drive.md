---
title: "Windows not picking up GParted formatted drive?"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-03-29
I installed a 2nd internal HDD to store media on and to allow a common files area to share between WinXP and Ubuntu.

I formatted the drive using Gparted as an extended partition and subdivided into 3, namely 1 Fat32 for iTunes library, 1 Fat 32 for WinXP/Ubuntu share, and the remainder as Ext2 for Ubuntu.

The 3 drives come up and are mounted in Ubuntu, however when I boot WinXP it doesn't recognise any additional drives other than C:/. Should it not pick up the FAT32 partitions?

What am I missing here?

---

### Post by pbpersson on 2009-03-29
> **aquascrotum said:**
> I installed a 2nd internal HDD to store media on and to allow a common files area to share between WinXP and Ubuntu.

I formatted the drive using Gparted as an extended partition and subdivided into 3, namely 1 Fat32 for iTunes library, 1 Fat 32 for WinXP/Ubuntu share, and the remainder as Ext2 for Ubuntu.

The 3 drives come up and are mounted in Ubuntu, however when I boot WinXP it doesn't recognise any additional drives other than C:/. Should it not pick up the FAT32 partitions?

What am I missing here?

So....on that drive you have NO primary partition?  Keep in mind that Ubuntu is a modern OS and allows you to color outside the lines.  You might want to do some research.....but I think a HD with no primary partition is a no-no in the XP world.

---

### Post by pbpersson on 2009-03-29
Whatever you do, don't go in the other direction and put three primary partitions on the drive!

I think based on my memory that XP expects the first partition to be primary and there can only be ONE primary partition.  I don't have the rules in front of me.

I would do:

Primary FAT32
Extended FAT32
Extended Linux

---

### Post by aquascrotum on 2009-03-29
Suspected that might be the case. I thought it was only a primary partition if you wanted to boot from it? Am a complete novice at this lark.

---

### Post by Moop on 2009-03-29
Windows doesn't require any primary partitions on a disk. 

Why not just create the partitions you want to share in ntfs?

 Also there are ways to access ext2/ext3 from windows. [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by egalvan on 2009-03-29
> **pbpersson said:**
>  You might want to do some research...
but I think **a HD with no primary partition is a no-no in the XP world**.

Sorry, not true. 
I've been running drives with extended-ONLY partitions since back in the old DOS 3.x days...

Windows never did like BOOTING from an extended...
but that's another kettle of fish...

There are other factors at work here.

Gparted Gurus, please chime in :)

ErnestG

---

### Post by egalvan on 2009-03-29
> **Moop said:**
> Windows doesn't require any primary partitions on a disk.

there are ways to access ext2/ext3 from windows. [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

I used to use this one...
*Ext2 Installable File System For Windows*

Unfortunately, it's not been up-dated, so large inodes give it troubles...

quote from their web site release notes:

[B]
 Large inodes
The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.
Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.
Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup. [/B]

---

### Post by aquascrotum on 2009-03-29
Well given the no primary partition theory is out the window, why isn't Xp picking up my FAT32 partitions?

---

### Post by Ugluk on 2009-03-29
What do you see in Disk Administrator snap-in in Windows? Describe or link screenshot.

---

### Post by aquascrotum on 2009-03-29
:oops: for me.

The 2nd SATA controller in the BIOS hadn't been enabled. When Ubuntu picked the drive up I assumed that it was enabled - when I checked it and enabled it XP loaded the partitions in fine.

Does Ubuntu somehow override the BIOS or something? Or how did it see the new drive before the controller was enabled?

---

