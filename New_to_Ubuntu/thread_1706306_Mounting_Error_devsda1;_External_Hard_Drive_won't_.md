---
title: "Mounting Error /dev/sda1; External Hard Drive won't mount"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by tracy602 on 2011-03-13
Absolute beginner, Ubuntu Netbook install running off the SATA NDC WD 1600 BEVT 22A23TO of a HP Mini 110-3000, mapped to /dev/sda1, mounted at /.  I can't read my external Seagate 500 GB harddrive; I tried to mount and get error message:   Error mounting: mount exited with exit code 1: helper failed with: mount: according to mtab, /dev/sda1 is already mounted on / mount failed  I was mucking about trying to get other USB keys to read, and I think I may have manually mounted my own hard drive to a USB port sda1 (I followed instructions at [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)).   I've tried the three other USB ports; same error message.  The drive also has some 'bad sectors' but I can't fix them until it's mounted.  Thanks for your help.

---

### Post by rosencrantz on 2011-03-13
Hi tracy602, where did you get that output from, a command-line mount? Can you post the exact syntax?
The /dev/sda1 stuff almost certainly relates to your system hard disk's primary partition, which is, of course, mounted - so did you do something like 'sudo mount /dev/sda1 /some/folder' (options omitted)? In that case, try /dev/sdb1 or rather /dev/sdb5 (the primary and extended partition on a secondary drive 'B') instead and see how that works...
A drive with physical errors can also screw up your mount, but then it's usually seriously corrupted. If you haven't already, you should probably back up important data as soon as you get the drive to mount.

Cheers,
rosencrantz

---

### Post by tracy602 on 2011-03-13
Thanks for your prompt reply rosencrantz... 

The error message comes from the Disk Utility.  I was using that because I had such difficulty figuring out how to open the contents of an external drive in terminal.  Can you tell me the command to get the exact syntax?  I'll cut and paste it here.  Thanks again!

---

### Post by rosencrantz on 2011-03-13
Ah, OK, I thought you had tried mounting from a shell... I don't have access to the disk utility (Kubuntu here), so I don't know how it's calling mount internally. Actually, Ubuntu should be rather good at automounting... How is the drive formatted?
I'd try mounting by hand first to see whether anything is wrong there:
(if you are unsure about the correct device identifier - I'll just use /dev/sdb5 -  try inferring it from the output of ls -l /dev/disk/by/id)
sudo mkdir /media/mydisk
sudo mount /dev/sdb5 /media/mydisk
If mount is able to infer the formatting correctly, this should give you read-only access. You can fiddle with permissions further (see e.g. here, [http://ubuntu.swerdna.org/ubufat32.html](http://ubuntu.swerdna.org/ubufat32.html)), or specify explicit formatting with mount -t vfat (or ntfs-3g, ext4 or whatever).

---

### Post by tracy602 on 2011-03-13
Worked like a charm!  Thanks so much for your help.  I also managed to get it to fix the bad sectors.  Big bonus.  :D

---

