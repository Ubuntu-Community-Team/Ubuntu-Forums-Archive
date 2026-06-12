---
title: "Dual boot XP Ubuntu : Defragmentation, Partitioning, EISA issues"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by khaktus on 2009-08-11
Hello,

I'm not completely new to the unix, but I'm trying to install Ubuntu on my laptop on Lenovo TP R500together with XP for the first time, here are my questions (that might be interesting to other Lenovo-Ubuntu users, as I didn't find much info on the web)/

1.
I declined from WUBI, as someone on some forum suggested, that it is slightly slower and limited compared to the dual-boot installation. (However I would like to know, **how Windows and Ubuntu are separated and how they share common files** - txt, doc, pics, movies - side of system files, if nothing is partitioned.)

2., 3., 4.
Dual boot XP Professional - Ubuntu Jaunty-Jackalope - on Lenovo TP R500 (250GB, @GB RAM) I imagine like this:
SDA1: 50GB XP (ntfs)
SDA2: 160GB Media (ntfs) - As I heard newer version of Ubuntu have no pb with ntfs and that fat32 (as usually suggested for the shared partition) is more prone to problems.
I plan to do this as extended partitons with logical p. for /, for swap (and I don't know if another l.p. for /home.
SDA3: 20GB Ubuntu (ext3)
SDA4: ??GB EISA (it is already there from manufacturer) - I searched a lot on google, but had pb. to find relevant info - just that this is inaccessible recovery partition.
Questions: 
[B]-Anyone has experience with EISA on Laptops? Is it necessary to leave one 1of4 primary partitions for it?
-No objections to suggested partitionig?
-No objection to shared partition NTFS?[/B]

**5.**** The biggest issue now:**
I had an issue with partitioning C: with windows sw, PageDefrag and PerfectDisc. 
First, there was something in the middle of the 250GB disc (otherwise almost empty), probably pagefile.sys and hyberfil.sys, which disappeared after stopping hibernation and paging options and doing PerfectDisc offline (reboot) defrag and afterwards online "Consolidate Space" option. The only remaining thing are some 2 grey-box **metadata**, that are remaining **in the middle of the disc**. **Cannot move them to the front of the disc (towards other data)**, I don't know what they are. I tried a few defrags online/offline, consolidation, with Avast AV off, no help. Windows/PageDefrag show nothing remaining in the middle of disc (as they showed previously with pagefile/hyberfil), only PerfectDisc sees these metadata. 
Any suggestions please? I heard an advice to repartition disc without worries, that these metadata are disc indexing files, that will be moved together with reducing C:/ disc space in GParted, but I don't want to overwrite something important.

[ATTACH]124445[/ATTACH]

[ATTACH]124446[/ATTACH]

[ATTACH]124447[/ATTACH]

Thank you (even for reading it all) :)

---

### Post by Cato2 on 2009-08-11
To be honest, a Wubi install would be much simpler and safer, and I'm sure the speed difference would be pretty small.  Ubuntu is generally faster than Windows on the same hardware.  However, for a laptop Wubi isn't so good as I think it stops suspend/hibernate working.

If you really do want to repartition, please do a thorough backup of everything - ideally use Acronis True Image to an external drive so you have a full image of all partitions.  Be sure to have your recovery CDs, license keys, etc, in case of a reinstall.

Your partitioning looks fine generally, though a separate /home partition of say 20 GB might be good.  Avoids any chance of Windows trashing your home directory and makes upgrades a bit easier, but is not essential.

The EISA partition is for recovery, and should really be left in place to recover your Windows setup - however if you went for True Image backups from Windows, and did a separate backup copy of the EISA partition, you could then delete it I guess.

NTFS is fine as a shared partition, it's a little slower than ext3 but that's OK for media files.  I would recommend putting your /home on the main / partition though, or ideally as separate partition.

No idea what the metadata is that you are seeing in PerfectDisc.  You might like to try burning a copy of Parted Magic and booting that, it has some good tools for viewing partitions etc, and is generally very good for repartitioning of XP.

JkDefrag is also good in Windows for defrag, it's as safe as commercial tools (they all use the same Windows API) and gives more info sometimes - use JkDefragGUI to install and run it, then look at the logs, as I think it shows NTFS metadata etc.

If you use Parted Magic having done backups you are pretty safe.  If all else fails and the XP filesystem remains stubbornly large, you could just create a folder within it for use from Ubuntu, and mount the XP filesystem using NTFS.  Not very elegant but it would work.  In fact that's a lot easier than repartitioning...

---

### Post by jacklinux on 2009-08-11
wubi would be my first choice. however the photo's look fine, i'll do some searching

---

### Post by khaktus on 2009-08-30
Problem solved (in a way): 
For the other users with same concerns:  

People from PerfectDisk contacted me while being in trial period (!) and offered help, after the consultation:  The advice is to find out what is the largest chunk of free space at the end of disk (let's say 113GB from 230), so substract it from total space, (230-113=...) and shrink a C:/sda1 partition in GParted to the size slightly bigger than the result. Then, reboot (2x, so that the Windows gets to normal), run PerfectDisk again (SystemFiles option, with reboot defragmentation) and after this is finished, You should end up with half a disk size of C:/sda1 and the mysterious metadata which is in fact **put by PerfectDisk in the middle of the disk** was now moved in the middle of the smaller-size disk.  

This is to be iterated until you get to the wanted size of the shrunk partition...  

Simply, shrinking partition towards metadata, then defragment system files and repeat...  

Thanks for your time.

---

