---
title: "4 primary partions already and want to install Ubuntu"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by HeyAZ on 2010-12-27
Have the same problem.
New HP i5 Pavilion laptop, 500G hard drive, Windows 7.  Want a dual boot, so here's my story!

First, put Ubuntu 10.10 64 bit onto the USB stick, works fine.
Then Win 7 full Disk Defrag.  
Now Shrink the Win7 C drive:
Control Panel > Admin Tools > Computer Mgmt > Storage > Disk Mgmt.
It offered to shrink it by about half, so Win7 would be on 237GB; accepted.  
It now lists the following for the disk: 
System		199 MB		ntfs
(C)		232.01 GB	ntfs
Unallocated	209.79 GB
Recovery (D)	23.66 GB	ntfs
HP_Tools	103 MB		FAT32

So now have a huge ~209 GB available for the Ubuntu install.
Rebooted Windows a few times, make sure all is OK, and changed the bios so the USB stick has priority.

Re-started booting from USB into Ubuntu, works great, can access the internet.
Install button.  “Erase and use the entire disk” obviously not the choice.
There is only one option: “Specify partitions manually (advanced)”  
Up comes the “Allocate Drive Space” screen, which lists:

/dev/sda
/dev/sda1	ntfs		208 MB		69 MB
/dev/sda2	ntfs		249123 MB	47521 MB
unusable			225260 MB
/dev/sda3	ntfs		25404 MB	21687MB
/dev/sda4	fat32		108 MB		33 MB

Its different sizes from what Microsoft Win7 reported, but have to assume close enough.  When I click on “unusable” which is the new unallocated space on the harddrive, the only option available is “Revert”.  The other 4 options are there but not accessible: New Partition Table, Add, Change, Delete.
Do I really want to hit that Revert button?  No, don’t think so; stuck. 
There is also a graphical format showing the same entries as the table except that instead of “unusable” it is called “Free Space” with 225.3 GB.
So cannot do the dual-boot installation.
  
sda4 appears the candidate for deletion, HP Tools, but does that affect running Windows?  
If I delete sda4 then will the unusable/ "Free Space" become available and the "New Partition Table" button become workable?
Should I delete this sda4 using the Win7 tools for Disk Management (and not the linux tool)?  
Will Win7 agree to let me delete sda4 or maybe its protected by the manufacturer HP?

Anybody have experience with this on HP?
Thanks, appreciate your insight.

...

---

### Post by wilee-nilee on 2010-12-27
**/dev/sda1 ntfs** 208 MB 69 MB
**/dev/sda2 ntfs** 249123 MB 47521 MB
unusable 225260 MB
**/dev/sda3 ntfs** 25404 MB 21687MB
**/dev/sda4 fat32** 108 MB 33 MB

4 primary partitions are the maximum on one HD. If you want real help start your own thread and follow this guide to get the bootscript posted. This will give us the correct information as since you have 4 partitions you have boot files spread around 3 of them.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

feel free to pm me when you get a thread started.:)

---

### Post by Sef on 2010-12-27
Moved post to own thread.

---

### Post by wilee-nilee on 2010-12-27
Hey your own thread, so post the bootscript and we can figure out the partition to remove and have it boot correctly.:)

Ask any questions if needed.

---

### Post by srs5694 on 2010-12-27
Your "Recovery" partition (/dev/sda3) almost certainly contains the copy of Windows that should be on one or more DVDs, but that your computer manufacturer was too cheap to provide in that form. There's probably a utility you can run to burn its contents to bootable DVDs, effectively backing up that partition. Run this utility -- twice. (Burned DVD+/-Rs are less reliable than pressed DVDs from a factory.) While you're playing human disc changer for your computer, write a letter to the computer manufacturer (with a cc: to Microsoft) telling them what you think of how incredibly cheap they are to not provide a proper recovery mechanism. (Think what happens to computers whose hard drives fail, thus removing the user's access to the Windows "installation medium.") They'll keep pulling this nonsense unless enough people complain, so please complain.

When this process is done, you should be able to safely delete that partition and create an extended partition in its place. (There's something to be said for moving /dev/sda4 earlier on the disk, so that the extended partition comes last, but this isn't absolutely required.) You can create as many logical partitions as you like inside the extended partition, and Linux will install just fine to a logical partition.

---

