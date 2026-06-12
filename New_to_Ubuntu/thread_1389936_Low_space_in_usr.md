---
title: "Low space in /usr"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by jaesjg on 2010-01-25
Hello everyone,

I use Karmic on a Compaq CQ40 laptop with an extra GB of RAM (totaling 2GB). Since I'm new I installed a lot of programs hoping to weed out the unwanted later. But now my system shows that '/usr has only 200 MB left' on boot up. My /usr is on a partition of 5.4 GB, and as far as I can see only 4.3 is being used.

My Hard Disk sections are as follows : 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31a431a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4080    32768000    7  HPFS/NTFS
/dev/sda2            4080       11601    60416000    7  HPFS/NTFS
/dev/sda4           11602       19457    63103320    5  Extended
/dev/sda5           18807       19457     5229094+  83  Linux
/dev/sda6           15857       18806    23695843+   b  W95 FAT32
/dev/sda7           11602       11725      995967   82  Linux swap / Solaris
/dev/sda8           11726       12723     8016403+  83  Linux
/dev/sda9           12724       15856    25165791   83  Linux

sda8 being system files, sda9 home, sda5 usr, sda 6 windows.

What should I do :

a. Uninstall all those (lovely) programs?
(I certainly won't, and plan to install more)

b. move a subdirectory of usr like /share which used 2GB! (what's up with that) to a newly created partition?
(I searched the forums and that is really daunting)

c.  extend my /usr (magically) (Is it possible?)( I have a live image of Jaunty)

I've attached a screenshot of my usr usage.

This is my first month of Ubuntu, and not only am I a newbie, but also a medical professional, so my computer skills are negligible.

Thanks in advance.

---

### Post by tom4everitt on 2010-01-25
I don't know why you get a warning if you, in fact, have more than a gig free. You'll probably need a bigger /usr sooner or later though, so:

b):

This is certainly possible. You can just put one of the subfolders on a different partion (which probably means you'll have to create one). Just edit /etc/fstab to get the partition to mount on the right place (there's lots of guides on this, just google). 


c):
Might be the easier solution, in case you have some other partion that you can shrink a few gig. Just boot from a live cd and open gparted. Its very easy to use gparted, it hardly needs to be explained. You can just shrink, grow and move partitions the way you want them by dragging them around. 

This may have the unpleasant effect of making you're system unbootable for a little while however, as the boot loader may not be informed of these changes. So you may have to restore grub in order for it to be bootable again. 



Fiddling with partitions from a live cd is a bit risky, especially as a newbie. There's only one way to learn however, and if you start and not being able to finish, there's usually someone in the forum being able to help you. But be prepared to be forced to reinstall the entire system. Keep a good back up before you start!

Good luck!

---

### Post by jaesjg on 2010-01-27
Had to reinstall after everything went down hill.

Though there are bad sectors in most partitions. Reformatting doesn't seem to help.

---

### Post by bodhi.zazen on 2010-01-27
> **jaesjg said:**
> Had to reinstall after everything went down hill.

Though there are bad sectors in most partitions. Reformatting doesn't seem to help.

Bad sectors is starting to sound like a failing hard drive. 

If re-installing did not work, time to back up any data you wish to keep and get an new HD.

---

### Post by adam814 on 2010-01-27
If you're being notified of bad sectors your disk is likely failing.  While I have seen some run for years with a few bad sectors it's unusual.

You could try (from a LiveCD) running "e2fsck -c -c /dev/<partition>" to have those bad sectors marked so as not to be allocated for a file or directory.  Of course that assumes you're using ext2, ext3, or ext4 (Ubuntu now uses ext4 by default).

---

### Post by jaesjg on 2010-01-28
Thanks guys, will do complete backup and change hard drive.

Which means I'll be divorcing Windows completely :)

Can this thread be closed?

---

### Post by adam814 on 2010-01-28
I believe you can mark it as solved under "Thread Tools" at the top of the page.  Threads here don't close and disappear in case others have the same issue and would find them useful.

---

