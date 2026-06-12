---
title: "[SOLVED] New Toshiba"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Bomgart on 2008-12-22
Hello,  I am completely new to Ubuntu... I am looking to install a stripped down operating system on my partitioned hard drive that I can boot from to go online and do online bill pay.  I think this ubuntu might do the trick.  I want to know if it is compatible with my laptob Toshiba Satellite L305D-S5897.  4 GB Ram, 250 GB HD, (8 GB already partitioned as FAT32) Running Windows Vista premium, AMD Turion 64 X2 Dual Core processor.  Any help would be greatly appreciated.

---

### Post by Her Ghost on 2008-12-22
there is no reason that it wouldn't be compatible.

download the Ubuntu Live Disc and try that first - if everything works after booting with that, you can install it no problem. If it doesn't work, you can either a) reboot and it's all gone or b) decide whether you have the time to spend getting it working :)

---

### Post by Bomgart on 2008-12-22
I actually downloaded the 8.??(cant remember) and booted it from a cd but it wants to partition... I already have it partitioned.  How do I intall it without it trying to partition?

---

### Post by Iowan on 2008-12-22
Partitioner *should* give option for manual partitioning.  Use that to insure existing partitions don't get overwritten.

---

### Post by Bomgart on 2008-12-22
Thank you!

---

### Post by Duck2006 on 2008-12-22
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by nhasian on 2008-12-22
you can do one of two things to try ubuntu without partitioning your hard disk.

1)  just boot off the liveCD that you downloaded and burned to disc.  Select the option to try Ubuntu without making any changes to the hard disk.  you wont be able to save any changes or preferences with this method, but you can test it out quickly on any pc.

2) you can boot into windows, and install wubi from there.  it will install Ubuntu in a file on your hard disk and then you can easily dual boot between windows and ubuntu.  later you can either use the add/remove programs tool in windows to remove ubuntu or you can move ubuntu to its own partition at a later date if you like it.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by fistfullofroses on 2008-12-22
I would heavily recommend not using FAT32 as a root filesystem for GNU/Linux. You would want to use a filesystem like ext2, ext3, reiserfs, jfs, zfs... These have far improved performance and reliability.

---

### Post by Bomgart on 2008-12-22
Whenever I tried installing I get to the manual and it brings up a list of drives ( I see the one I partitioned using vista) it is listed as FAT32.  Ubuntu gives me the option of deleting or editing... If I pick fat it says something about no root...??

---

### Post by Duck2006 on 2008-12-22
> **Bomgart said:**
> Whenever I tried installing I get to the manual and it brings up a list of drives ( I see the one I partitioned using vista) it is listed as FAT32.  Ubuntu gives me the option of deleting or editing... If I pick fat it says something about no root...??

In the install you use manual partition
high light the partition delete the partition
high light the partition and chose new resize the partition to what size you want and click format then the box under that click the down arrow and chose / that is the root, so you end up with a

/ root partition
linux swap partition.

---

### Post by Bomgart on 2008-12-22
Thanks... I will try that.

---

### Post by Bomgart on 2008-12-22
Ok... 1/2 there... After I did the above... Now it says I do not have an partitions for swap... How do I fix that?  Was I suppose to make two partitions?

---

### Post by Duck2006 on 2008-12-22
> **Bomgart said:**
> Ok... 1/2 there... After I did the above... Now it says I do not have an partitions for swap... How do I fix that?  Was I suppose to make two partitions?

Yes, resize your /root partition to give you a swap partition and then see how it goes.

---

### Post by Bomgart on 2008-12-22
I have 8 GB how much should swap have?

---

### Post by Duck2006 on 2008-12-22
> **Bomgart said:**
> I have 8 GB how much should swap have?

I use round 1Gb try that and see if it works for you, If not you can always resize it later.

---

### Post by Bomgart on 2008-12-22
> **Duck2006 said:**
> I use round 1Gb try that and see if it works for you, If not you can always resize it later.
What should the mount point be for swap? /boot; /home; /tmp; /usr; /var; /srv; /opt; /usr/local?

---

### Post by Duck2006 on 2008-12-22
> **Bomgart said:**
> What should the mount point be for swap? /boot; /home; /tmp; /usr; /var; /srv; /opt; /usr/local?

Yes the mount point linux swap. so you should have

/ is your root partition (what size you want)
linux swap 1Gb

---

### Post by Bomgart on 2008-12-22
I already have / it is 7 GB.  I need to know what mount point I use for swap?

---

### Post by Duck2006 on 2008-12-22
> **Bomgart said:**
> I already have / it is 7 GB.  I need to know what mount point I use for swap?

Yes, The mount point for the swap partition is linux swap, where you make the point for /root go down the list and you will see swap.

---

### Post by Duck2006 on 2008-12-22
[http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1](http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1)

---

### Post by Bomgart on 2008-12-22
I was getting the ID-ten-T error (IDIOT).  I had to click on the box that had ext3 and change that to swap.  I'm good now... It is installing!  Thanks for all your help!

---

