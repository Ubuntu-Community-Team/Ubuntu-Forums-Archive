---
title: "partitioning 320gb - help"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by kimikrishna on 2010-09-11
HI,

I have bought a new dell inspiron 15 r laptop withOUT windows 7 preinstalled B-)

It has 320 gb harddisk.

I want to know some suggestions on partitioning and to know my idea on this will work correct..

One extended for ubuntu  : [root,home,swap]
next one extra ext4 primary
then one ntfs primary
then one ntfs primary. 

ntfs because i may want to install windows7 later.

Is this correct?

(I have never partitioned a NEW harddisk before....)

---

### Post by jtarin on 2010-09-11
Sounds good! Give you some time to see if you want more space for Ubuntu, but remember...Windows likes to be first partition.

---

### Post by Rubi1200 on 2010-09-11
Agree with jtarin. 

Also look here for general information:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good luck and don't forget to always backup important data.

---

### Post by kimikrishna on 2010-09-11
Then the two ntfs be on top
and then ext4 
Can the extended partition be in the **_end_** which will hold root,swap, home?

---

### Post by coffeecat on 2010-09-11
> **kimikrishna said:**
> Then the two ntfs be on top
and then ext4 
Can the extended partition be in the **_end_** which will hold root,swap, home?

Sounds good. As someone has already said, it's best to put Windows in the first primary partition - in fact it has to be primary for Windows to boot. If you leave the Windows 7 installer to its own devices it will make a separate small boot partition, but you can install Windows 7 to one primary partition if you wish. So..

Partition #1 - primary ntfs = Windows C:
Partition #2 - primary ntfs - I presume this is for a shared Data partition.
Partition #3 = extended partition.

And then put all your Linux partitions as logical partitions in the extended #3. Linux is quite happy with logical partitions. In fact that layout is what I do. :)

---

### Post by jtarin on 2010-09-11
That's how mine is setup also.

---

### Post by coffeecat on 2010-09-11
@kimikrishna, I just noticed this in your first post:

> **kimikrishna said:**
> 
ntfs because i may want to install windows7 later.


You may know this already, but there's one gotcha if you install Windows after Ubuntu. Windows will blithely overwrite the mbr and you will only be able to boot into Windows. This is easily fixed, and you'll also then have to regenerate the grub menu to get a Windows entry, but that's all part of the grub repair procedure. When you're ready to do this, start a thread and someone will help you through it - if you need.

Good luck!

> **jtarin said:**
> That's how mine is setup also.

Great minds and all that! :p

---

### Post by kimikrishna on 2010-09-11
Big thanks to everyone who replied me!

---

### Post by srs5694 on 2010-09-11
Since you say you *may* want to install Windows *later,* I wouldn't create any NTFS partitions *now.* The reason is that Linux has very poor NTFS maintenance tools. Thus, if you try to use those partitions, you could well end up in a situation where they become completely inaccessible if there's a system crash. Linux won't access them until they've been checked by Windows, and without a Windows installation, you'll end up running around looking for a Windows emergency disc you can use.

Instead, either create the partitions using a Linux filesystem and plan to clear them out and convert them to NTFS if/when you decide to install Windows; or leave the space unpartitioned until you do install Windows. Of course, if you don't use the space, putting NTFS partitions there won't really do any harm; but *using* NTFS partitions on a Linux-only computer is asking for trouble.

---

### Post by rocknrollmouse on 2010-09-11
My method for setting up machines is to set up the partitions how I want them (usually using gparted live disk), do a quick install of Windows on the Windows partitions (allow Windows to re-format them), then install linux distro of choice for that box.  

This allows me the control over partitioning I like from gparted; Windows is happy as it has formatted the partitions how it like them; and my chosen distro loads and configures boot correctly. :)

Once the O/S's are loaded I can then configure environments and load software as required.  (Usually linux first as its quickest and gives me a working machine that much quicker; I then finish loading Windows when I have the time or need.)

---

### Post by kimikrishna on 2010-09-12
@srs5694

Then can it be two fat on top instead of ntfs? 
Does linux like fat?

---

### Post by srs5694 on 2010-09-12
Linux's support for FAT is better than its NTFS support; however, FAT is a much older filesystem with limitations that can be important. Most notably, you can't store files larger than about 4GB on FAT, so it's not very good for big backup or multimedia files.

---

