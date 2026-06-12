---
title: "Lucid direct install vs. upgrade"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by dwalby on 2010-05-17
I'm running a dual-boot Vista/Ubuntu using Acronis OS Selector as a boot manager (its a bit dated but still works so for now I'm using it).  From what I've been told Acronis Disk Director (from which OS Selector is installed) is not compatible with ext4 at all, and only with the 128-bit inode version of ext3, not the 256-bit version.  My initial install was 9.04, then upgraded to 9.10, then upgraded to 10.04, all through the upgrade manager.  In other words, the only install from ISO disk was 9.04.  This works normally as far as I can tell, I haven't seen any problems with it.
 
However, I recently tried with a clean partition to install 10.04 directly from the ISO, which appeared to complete successfully.  I created two ext3 partitions, one for swap, one for / using Disk Director.  Then I installed 10.04 with format partitions unchecked as part of the install process.  I put GRUB in the / partition, not the MBR.  This is exactly the same method I used for installing 9.04, but now OS Selector doesn't recognize the Linux partition as containing an OS and will not boot it.  
 
So for now I retraced my steps back through the 9.04 install and upgrade path back to 10.04, and all is well again. 
 
Any idea what is different about installing 10.04 that would cause these symptoms?  I think all the Ubuntu versions are still backward compatible with ext3, even if they support ext4, right?  Does 10.04 use a newer version of GRUB that OS Selector just doesn't recognize?  If so I guess I could just load GRUB to the MBR and get rid of OS Selector altogether.

---

### Post by jerome1232 on 2010-05-17
10.04 does use grub2.

---

### Post by Kafubie on 2010-05-17
Upgrading can sometimes rarely...  not work and corrupt files.

Fresh installing it works perfect everytime, just is too boring setting your personal preferences again.

---

