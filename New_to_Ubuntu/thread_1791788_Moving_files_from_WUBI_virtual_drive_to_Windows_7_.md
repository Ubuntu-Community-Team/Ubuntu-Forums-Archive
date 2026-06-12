---
title: "Moving files from WUBI virtual drive to Windows 7 folder"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by AJYoung on 2011-06-27
Hello,

I am having trouble with dual boot Windows 7 and Ubuntu 11 on a netbook.  I had some trouble installing Ubuntu and tried via WUBI and ubuntu-11.04-desktop-i386.iso.  When I look into installed programs in the control panel I see Ubuntu listed as a program, which leads me to believe that WUBI worked.

After a restart, Ubuntu worked.  I copied a huge number of music files into the music folder in Ubuntu and eventually shut down.  Things seemed to be working fine.  I was able to access Ubuntu only two times in total.  Now, if I choose Ubuntu  from the boot menu, it doesn't load.  In regular mode I get a black screen with a blinking cursor.  In recovery mode I get a lot of script and then a blinking cursor at the end; no prompt.

What I want to do is copy all those music files into my music folder in Windows.  I tried the [COLOR=RoyalBlue]_[wubildr]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")_[/COLOR] overwrite patch to load Ubuntu (so I can move the files to a memory card), but this didn't work.  Failing this I thought I could try to find the files through Windows instead.  I tried using explore2fs, but I either can't use it properly or it's not working. Then I was able to install [COLOR=RoyalBlue]_[Virtual Volumes]("http://ubuntuforums.org/showthread.php?t=436923")_[/COLOR] (maybe this is the same as explore2fs?) as described in the link and can see the files and locate the root.disk and swap.disk files in C:\ubuntu\disks but if I try to double-click on the root.disk the program freezes and goes into unresponsive mode.

I am a complete beginner with dual-boot systems, but I understand that Ubuntu through WUBI is not a partitioned section of my hard drive, but is in fact launched as a program from Windows.  I plan on getting rid of this (uninstalling Ubuntu in Windows), partitioning and installing it separately, but I want to recover these files first.  This is what I need help with.  I considered migrating WUBI into a full partitioned OS but I fear it will be too complicated for me and/or will not bring all the music files with it.

I am not a programmer and barely grasping what I am doing, so I need very clear instructions.  I appreciate any help.

Thank you,

Aleksandra

---

### Post by Mark Phelps on 2011-06-27
You should be able to see your Windows partition located at /host with Nautilus -- and then drag and drop your files there.

---

### Post by bcbc on 2011-06-27
Is this the one you used? [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)
That works on ext4 file systems.

If that fails, create a bootable CD or USB from that ISO you downloaded and mount the root.disk using that. The [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") explains how to identify the partition that contains the root.disk and then how to mount it.

---

### Post by AJYoung on 2011-06-30
Thank you both for your suggestions.  I will try when I get a chance (I don't always have a connection here in Turkey) and get back to you if I am unsuccessful.

---

### Post by AJYoung on 2011-08-06
> **Mark Phelps said:**
> You should be able to see your Windows partition located at /host with Nautilus -- and then drag and drop your files there.

Hi Mark (or anyone else who can help),

As I expected, I'm confused.  Where is Nautilus? In Ubuntu?  If so, then this won't work because I can't boot Ubuntu (in either safe or regular mode).  Also, I didn't think the drive was partitioned at all since I'm using WUBI.  Is that not the case?

Aleksandra

---

### Post by bcbc on 2011-08-06
Use that tool I referenced and point it at the Wubi virtual disk: C:\ubuntu\disks\root.disk
(change C: if you installed on a different drive)

If you still cannot read it:
1. run chkdsk (right-click on C:, Properties, Tools, Check disk for errors, fix automatically, reboot to complete check)
If you still cannot read it:
2. [fsck]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F") the root.disk from a live CD

---

