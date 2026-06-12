---
title: "Windows Reinstall"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by shubhbansal on 2011-03-30
Hi

A virus has caused me to have to reinstall windows. I currently have 3 OS's installed on my system: Windows, Ubuntu (1) and Ubuntu (2-the wubi kind). (Side Note-Ubuntu(1) sort of stopped working because I had allocated too little space while installing it, and I didn't think it was worth meddling in boot loaders and partition managers to uninstall it.)

Among the recovery options that came with my notebook, I can only restore the Windows partition to its original state, not repair my windows installation, and since Ubuntu(2) and windows share the same partition, I'd like some way to preserve Ubuntu(2).

I have read on forums that an easy way to do this is as follows:
1. Backup the Ubuntu iso present in the windows partition.
2. Reinstall windows, reinstall wubi.
3. Replace the new wubi's installed files by the backed up Ubuntu(2) files.

My questions are- 
1. Would this work given my system? I have 3 OSs, three levels of BOOT menus etc.
2. Now that I'm reinstalling windows, I'd also like to know if there's an easy "Risk-free" way to get rid of the Ubuntu(1) partition. Risk Free because I just don't have enough external hard disk space to backup all my data, and even though I have backed up critical stuff, I still wouldn't want to lose anything.

Total Noob, simple, detailed instructions much appreciated.

Thanks!

---

### Post by Frogs Hair on 2011-03-30
Wubi installs Ubuntu inside the  Windows partition . If you are going reformat and reinstall Windows  Ubuntu will be completely removed.

If you would like to continue to use Wubi start fresh after Windows has been reinstalled .

---

### Post by bcbc on 2011-03-31
> **shubhbansal said:**
> 
I have read on forums that an easy way to do this is as follows:
1. Backup the Ubuntu iso present in the windows partition.
2. Reinstall windows, reinstall wubi.
3. Replace the new wubi's installed files by the backed up Ubuntu(2) files.

My questions are- 
1. Would this work given my system? I have 3 OSs, three levels of BOOT menus etc.
2. Now that I'm reinstalling windows, I'd also like to know if there's an easy "Risk-free" way to get rid of the Ubuntu(1) partition. Risk Free because I just don't have enough external hard disk space to backup all my data, and even though I have backed up critical stuff, I still wouldn't want to lose anything.

Total Noob, simple, detailed instructions much appreciated.

Thanks!

You can transfer a wubi install... but if you do a system restore on your PC it may well replace all partitions, not just the windows partition. So unless you can backup externally, you could lose everything.
Plus I would never risk any sort of partitioning/system restore without taking a full backup. You shu

The thing with Wubi is that the root.disk contains the boot menu it requires to boot, and it's aware of the partition it's on. But it's simple to modify this on the fly.

Here're some instructions (assuming you just have the single virtual disk): [http://ubuntuforums.org/showpost.php?p=10584729&postcount=4](http://ubuntuforums.org/showpost.php?p=10584729&postcount=4)

---

### Post by shubhbansal on 2011-03-31
Okay, the instructions seem simple/clear enough...

Could you also help me out with the second issue?
I already knew that you could do *something* like this to restore wubi, but the problem is my that case is slightly different. 

Before I reinstall windows, I plan to format and then merge the Ubuntu(1) partition with the new windows partition. 

1. What would be a good way of formatting the Ubuntu(1) partition and merging it with the formatted windows partition?
2. Could this change things regarding the wubi restoration? The fact that in my new system the no. of partitions etc. will be different.

---

### Post by bcbc on 2011-03-31
The trick is whether you're using Grub to boot. If so, then formatting the Ubuntu partition will stop your computer booting.

I'd first make sure that the computer boots straight to windows (or the windows boot manager) - not grub. If you see the grub menu, you need to install the windows boot loader or equivalent.

You can't merge the partitions while you're running Windows (if it's XP). If it's vista/7 I guess you would go to the disk manager, delete the Ubuntu partition, and then merge the free space with your windows partition. If you're on XP you'll need to boot a CD with a partitioning tool (e.g. Ubuntu and use GParted) to do it.

Re. Wubi... If you follow the steps in that other thread, then it won't matter to Wubi whether the partitions have changed. (That's why there's that extra step of installing a fresh wubi, checking it's own grub menu to confirm the partition) and then apply those settings to the backed up wubi.

---

### Post by shubhbansal on 2011-04-09
Update:

I ended up backing up my entire system and completely restoring it (using the recovery partition my Vaio had).

A problem I encountered was that on restoring my windows partition, the partition on which wubi was installed, my GRUB got corrupted as a result of which I couldn't boot to *any *OS. (as bcbc had pointed out earlier. althouth it was difficult for me to use his proposed solution as I didn't have access to any running os)

I solved this by installing ubuntu on another partition, and this replaced GRUB and all was well.

---

### Post by matty abbo on 2011-04-09
you could try to back up the files in the ubuntu installations and reinstall XP to its original state then reinstall ubuntu and put the files back where they came from

---

