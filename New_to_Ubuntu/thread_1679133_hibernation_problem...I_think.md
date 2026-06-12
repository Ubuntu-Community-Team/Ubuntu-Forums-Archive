---
title: "hibernation problem...I think"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by antiprice666 on 2011-01-31
I just set up my computer to dual boot (Windows XP and Ubuntu 10.04.1 LTS) for the first time.  I am able to dual boot fine although my partitioning my be "sloppy".  There were a couple hang ups but with the help of this forum I got everything working.  I am now in the installing drivers and adding Firefox plugins stag.  I "think" I am doing ok.  No crashes or lockups.  The only problem I am having now is when my computer goes into hibernation I get error messages and it powers down.  The messages are:

hub 4-2:1.0:hub_port_status failed (error= -62)
^this messages repeated multiple times^
pm_op():usb_dev_thaw+0x0/0x20 returns -62
(some more lines of code)
PM:device 4-2 failed to hibernate:error -16
power down

I'm not sure where to look for the problem.  The only thing is can think of would be my partitions maybe.  I have 1 for windows and 3 for Ubuntu.  I made all of them primary (not sure if this has any relevance) because I didn't know better.  The Ubuntu partitions are /, /home, and swap.  I was told to make the swap partition equal to my ram (4 gigs) but when I made it it isn't exactly the same size.  Not sure if this is the problem.  I just read that the only time I would need a swap partition is if I plan to use hibernation.  If the easy fix is simply turning off hibernation that could be an answer but I'm actually finding the "learning" part of this whole switch to be fun so I would like to fix the problem if I can.  That is if it's not too crazy techinical.  I just opened pandora's box so to speak so my tech knowledge is minimal at this point.

---

### Post by mharrison on 2011-01-31
I don't think this is a partition problem.  Try this, reboot and when Grub comes up, select an older kernel version to boot into Ubuntu and then try to hibernate.  I recall reading one of the newer kernels had some problems hibernating but I cannot confirm.  If nothing else, it helps you eliminate something. 

If it does hibernate on the older kernel version, you may have to set that one as the default grub entry (we can work on that later) or you can wait until a fix is released.

---

