---
title: "External Hard Drive Won't Mount on Karmic, Macbook 2,1 Again!"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Vanessa1 on 2010-09-03
Hi everyone, 

Earlier this year I encountered a problem with my external hard drive;  it would not mount automatically and I kept getting an error message.  Last time I was able to fix it by typing in the terminal 'sudo fsck  /dev/sdb2'. Once again it's not mounting automatically and I'm not even  getting the error message. I can't format the drive because I have  important data on it. The drive is 1TB Select USB 2.0 Desktop Hard Drive from Iomega. 

Also, I plugged in the drive, typed the command "sudo fdisk -l" in the terminal, and received the following:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d1620

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         977   ef  EFI (FAT-12/16/32)
/dev/sda2   *           1       13995   112413086   83  Linux
/dev/sda3           13995       14594     4806727+  82  Linux swap / Solaris

I have no clue what's wrong with it now. I've tried to fix it the same way that I did last time, but it's not working. 

I've been researching through forums and Google searches, but I haven't come across anything helpful yet. 

Thank you for your help!

---

### Post by Vanessa1 on 2010-09-03
I just solved the problem. Thanks!

---

