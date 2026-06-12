---
title: "How to backup/restore GRUB in Meerkat??"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by Casey R on 2010-11-10
Hey guys...need some help. Relatively new to Ubuntu so need a walkthrough on this if possible. Many thanks in advance!

I have Ubuntu 10.10 64bit and Windows 7 64bit dualbooted currently. 

What I want to do, is wipe the Windows partition, resize the partitions to have more space available in Ubuntu, and then reinstall Windows 7 from the DVD. I figure to save hassle, I'll simply create another EXT2 partition from the space allocated to Windows currently and have three partitions instead of 2. Is this the best way to go about this?

Now, I've read that reinstalling Windows will remove the Grub bootloader, making my Ubuntu installation inaccessible. From what I understand, I have to backup the GRUB bootloader from Ubuntu first....and then, after I install Windows, I'll have to boot from an Ubuntu Live CD, and then restore the GRUB bootloader?

So basically I just need the steps on how to back up GRUB and how to restore it when booted into the Live CD. 

Thanks!

Casey

---

### Post by Quackers on 2010-11-10
Would shrinking the W7 partition be an option? You can do it using Windows Disk Management console.

---

### Post by azertyh on 2010-11-11
hello,
the answer is in the doc [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

