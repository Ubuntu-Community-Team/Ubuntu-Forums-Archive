---
title: "Did Jaunty kill my hard drive, or is it just bad?"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2009-09-22
My comp died today, grub throws error 2 and when I try to mount the *dead* partition, I get an error.  A tail of dmesg is at the bottom.

Now, what's weird is when 9.04x64 was released I upgraded and started getting HDD corrupt type errors.  I freaked, formatted, and switched back to 8.10x64 and had no issues.  This week I decided to try 9.04 again.  Today, after about 7 hours or normal operation, X started acting very strange.  I tried logging out and got an "X could not be restarted" type BSOD.  Then Grub started giving error code 2.

I use 9.04x64 with the nvidia drivers (180, i believe), on an Asus x83v laptop.  Any ideas?  Did my HDD die or is something else going on?

ubuntu@ubuntu:~$ dmesg |tail
[  187.346997] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
[  187.346998] 
[  187.346999] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[  187.347290] ufs_read_super: bad magic number
[  187.350311] hfs: can't find a HFS filesystem on dev sda5.
[  220.243302] mtrr: no MTRR for d0000000,10000000 found
[  221.794027] lp: driver loaded but no devices found
[  221.888269] ppdev: user-space parallel port driver
[  257.041369] EXT3-fs error (device sda5): ext3_check_descriptors: Block bitmap for group 0 not in group (block 1114114)!
[  257.041677] EXT3-fs: group descriptors corrupted!

---

### Post by tomBorgia on 2009-09-22
Hi,

What did you format the disk as? Seems to be mounting as UFS then giving Ext3 errors???

Anyway probably is a disk problem... If you need to recover stuff try testdisk (for recovering partition data)...

---

### Post by beetlejuice_masterson on 2009-09-22
Thanks for the reply, tom -- yeah, i had it formatted as ext3.  It was running jaunty fine all day (and had run it fine the two or three other times I booted into it).  Then the hard drive seemed to die.

I wonder if it is loading as ext3, given the last two lines:
EXT3-fs error (device sda5): ext3_check_descriptors: Block bitmap for group 0 not in group (block 
[ 257.041677] EXT3-fs: group descriptors corrupted!

Any idea what could have happened here?  Any forensic gurus?  I will run disk surface test this evening.

---

### Post by tomBorgia on 2009-09-22
Whats the output of 

```
testdisk /list /dev/sdX 
```

(you may need to be root & have testdisk installed from synaptic / apt)

---

### Post by beetlejuice_masterson on 2009-09-23
ran e2fsc -c /dev/sda5

found 10 inodes containing multiply-claimed blocks, all in ~/.mozilla/firefox/???/
lots of unattached inodes
lots of inode ref counts wrong
tons of free block counts wrong
tons of free inodes count wrong & directory count wrong

i tried install testdisk but ubuntu wouldn't connect to the internet on the livecd :-/ .  what does it all mean?

---

### Post by beetlejuice_masterson on 2009-09-23
Update:
so, after fixing that stuff, GRUB came back and i was able to boot into ubuntu and download testdisk and run.  Seems like nothing abnormal here:
Disk /dev/sda5 - 61 GB / 57 GiB - CHS 7522 255 63, sector size=512

Disk /dev/sda5 - 61 GB / 57 GiB - CHS 7522 255 63
     Partition			Start        End    Size in sectors
   P ext3                     0   0  1  7522 166 24  120851412


The question remains:

How did everything get so jacked in the first place?

---

### Post by beetlejuice_masterson on 2009-09-23
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209346](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209346)

How to fix:
upgrade kernel to 2.6.29rc1 or better

My final thoughts?
linux, you're such a guy.

---

### Post by tomBorgia on 2009-09-23
Glad you got it fixed anyway.

Tom.

---

