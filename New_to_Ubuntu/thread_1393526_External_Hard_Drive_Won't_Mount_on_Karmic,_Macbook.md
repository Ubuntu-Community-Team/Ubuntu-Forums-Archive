---
title: "External Hard Drive Won't Mount on Karmic, Macbook 2,1"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by Vanessa1 on 2010-01-29
Hi! 

I'm hoping that someone can help me manually mount or fix my external hard drive. I can't format the drive because I have important data on it. The drive is 1TB Select USB 2.0 Desktop Hard Drive from Iomega. When I plug it in, a message appears that reads: 

"Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail  or so". 

I've been researching through forums and Google searches, but I haven't come across anything helpful yet. 

Thank you for your help!

---

### Post by blazemore on 2010-01-29
Can you please post the result of running the command@
```
sudo fdisk -l
```
with the device plugged in.
Thanks.

---

### Post by Vanessa1 on 2010-01-29
Sure. I plugged in the drive, typed the command in the terminal, and received the following:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d1620

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         977   ef  EFI (FAT-12/16/32)
/dev/sda2   *           1       13995   112413086   83  Linux
/dev/sda3           13995       14594     4806727+  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1          121560      121561        8192+  82  Linux swap / Solaris
/dev/sdb2   *           1      121560   976426672   83  Linux

Partition table entries are not in disk order

I have no idea what it all means? 

Thank you for your response and help!

---

### Post by Vanessa1 on 2010-01-31
Someone suggested that I run the command 'sudo fsck /dev/sdb2', which I did and I typed 'y' (yes) to all the prompts. It fixed the problem, and I'm able to mount the hard drive again! Plus, my data is all there! 

Thanks!

---

