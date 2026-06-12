---
title: "2 Ubuntu Boot Options"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by Ronnicus on 2010-02-18
I'm not exactly sure what happened, but now when GRUB boots up and gives me the list of Operating Systems to choose from, I get two options for Ubuntu?
 
The screen looks like this:
Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Microsoft Windows XP Professional (on /dev/sda1)
 
 
Worst of all, when I pick the first one, my computer spits out a bunch of weird code instead of loading Ubuntu.
 
It goes...
 
udevadm trigger is not permitted whiel udev is unconfigured
udevadm settle is not permitted whiel udev is unconfigured
svgalib: Cannot open /dev/mem.
Gave up waiting for root device. Common problems:
- Boot args(cat/proc/cmdline)
-Check rootdelay=(did the system wait long enough?)
-Check root=(did the system wait for the right device?)
-Missing modules (cat/proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/ae29de5e-b684-40e7-a60f=78133542f08e does not exist/ Dropping to a shell!
 
BusyBox v1.13.3 (Ubuntu 1:1.13.3=1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs) *waits for user input*
 
 
Can anyone help me with this problem? I'm not sure if it's an error with my partitions or something. I only recently installed Ubuntu.
 
Thanks

---

### Post by Ronnicus on 2010-02-18
Bump. Any suggestions?

---

### Post by WubiNoob on 2010-02-18
I'm not an expert at these codes, but I think you might have accidently installed Ubuntu twice if you're getting it twice in your grub menu. One is clearly not working, how about the other? If you did not install it twice, you may want to see what recovery mode in that partition that holds the problems. I hope this helps.

---

