---
title: "Install ubuntu 8.10 on second hard disk"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by davidtuti on 2008-12-05
Hi,

I have 2 hard disks SATA. On a sata disk I have one partition with Windows XP. I would like to install Ubuntu on the other Sata - Disk. 

Could you say me if I have to do something to these installation of if there is some problem with this instalation?

Many thanks and sorry for my english!

---

### Post by Kobalt on 2008-12-05
Hello,

There are no problems at all installing Ubuntu on your second hard drive : just point the Ubuntu installer to this place where you want it to install, and rock and roll :)

Cheerio.

---

### Post by irw on 2008-12-28
> **Kobalt said:**
> There are no problems at all installing Ubuntu on your second hard drive : just point the Ubuntu installer to this place where you want it to install, and rock and roll :)

If only it was so easy - on my system, the standard or alternative install CDs do not offer the second HD during the install.

If I use the partition Editor from the System menu, or work at the command line, then all partitions and disks are shown correctly; it is only the install partitioner that does not seem to work.

Any Suggestions?

---

### Post by mapes12 on 2008-12-28
> **irw said:**
> If only it was so easy - on my system, the standard or alternative install CDs do not offer the second HD during the install.

If I use the partition Editor from the System menu, or work at the command line, then all partitions and disks are shown correctly; it is only the install partitioner that does not seem to work.

Any Suggestions?
irw - is your second HDD internal or external. Also, has it been formatted with the ext3 file system?

---

### Post by irw on 2008-12-28
I have an HP Pavilion laptop with two internal hard disks.

The first is setup with an encrypted install using an ext3 boot partition, the rest encrypted LVM; the second has a number of partitions, the first three of which are ext3, the forth is encrypted.

---

### Post by bwallum on 2008-12-28
Just to say I have installed on a second hard drive for running a development snap shot of Ubuntu. The only problem I encountered was the need to format the new drive. I did this with gparted (available in the repos as Partition Editor). I formatted all of it to ext3. Then I ran the install cd and installed Ubuntu on the second drive.

I have had issues with the Intrepid live cd (64bit) and at one stage had to first use a Hardy live cd then upgrade online.

It is possible that a new drive can be formatted in windows to say fat32 format then when installing Ubuntu change the format to ext3.

Hope some of that helps

---

