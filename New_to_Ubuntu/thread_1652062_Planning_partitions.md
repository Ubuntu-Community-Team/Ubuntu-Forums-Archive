---
title: "Planning partitions"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by Gforgio on 2010-12-24
Hi everyone, 

i have been trying to read by my self, how to properly prepare my hard drive, but I still have one big question. 
I just bought a new hard drive and I would like to install first Ubuntu on it, and then at some point windows 7. 
Of what I have understood I should use a primary partition with NTFS where I should be able to install windows later on, but while I'm installing linux and partitioning my drive, I don't see anywhere NTFS, just Ext4, Ext3, FAT, swamp and so on.. 

So my question is: should I just "not use this partition" or what should I do, to be able to later on install widnows 7 into a partition? 

Thanks.

---

### Post by amjjawad on 2010-12-24
> **Gforgio said:**
> Hi everyone, 

i have been trying to read by my self, how to properly prepare my hard drive, but I still have one big question. 
I just bought a new hard drive and I would like to install first Ubuntu on it, and then at some point windows 7. 
Of what I have understood I should use a primary partition with NTFS where I should be able to install windows later on, but while I'm installing linux and partitioning my drive, I don't see anywhere NTFS, just Ext4, Ext3, FAT, swamp and so on.. 

So my question is: should I just "not use this partition" or what should I do, to be able to later on install widnows 7 into a partition? 

Thanks.

Hello and welcome :)

First of all, kindly read this link: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

It will help you to understand more about this issue as you're required to learn the basics first.

Second of all, on my signature, there's a Dual Booting Guide. Please read it.

You still can install Ubuntu "first' then Windows after that but there are few simple tricks.
However, if you're planning to install Windows later on, you can prepare your HDD from now.

Simple Example:
Say you have 300GB HDD.
You can use 100GB for Ubuntu (root partition, home partition and swap partition - please refer back to the first link I posted)
100GB for Windows (that partition MUST be Primary)
100GB for your data/files and it's shared between both Windows and Ubuntu.

It's all up to you.
If I were you, I would do it this way:

sda1: Type: NTFS - Primary Partition - will be used for Windows
sda2: Type ext4 - Primary Partition - will be used as / (root) partition for Ubuntu
sda3: Extended Partition
sda5: Type ext4 - Logical Partition - will be used as /home partition for Ubuntu
sda6: Type SWAP-LINUX - Logical Partition - will be used as swap partition for Ubutu
If you want > sda7: Type NTFS - Logical Partition - will be used to shore your data files and can be accessed by both Ubuntu and Windows.

---

### Post by Sunships on 2010-12-24
"Do not use" the partition that you intend to use for Windows. The Windows installer should be able to format that partition appropriately. 

HOWEVER, be warned that installing Windows AFTER installing Ubuntu will probably mess up the GRUB boot loader. It's generally easier to install Windows first, then Ubuntu. If you are set on installing Ubuntu first though, make sure you back up anything important from your Ubuntu install beforehand (consider using Remastersys to re-install your existing Ubuntu system after installing Windows) and read up on restoring the master boot record/boot menu and re-installing GRUB. There might be a guide for doing this somewhere on the forums.

---

### Post by amjjawad on 2010-12-24
> **Sunships said:**
> HOWEVER, be warned that installing Windows AFTER installing Ubuntu will probably mess up the GRUB boot loader. It's generally easier to install Windows first, then Ubuntu. If you are set on installing Ubuntu first though, make sure you back up anything important from your Ubuntu install beforehand (consider using Remastersys to re-install your existing Ubuntu system after installing Windows) and read up on restoring the master boot record/boot menu and re-installing GRUB. There might be a guide for doing this somewhere on the forums.

Yes, definitely installing Windows "first" is easier but still you can do it the other way around. Fixing GRUB2 is very easy indeed.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Gforgio on 2010-12-24
Yeah, I read that windows mess up with everything if you install it later on, but I it seems its not that difficult to recover Ubuntu after all... I will try it that why, and yep, my question was whether for the Windows partition I should use the "do not use" option,  because the NTFS is not showed directly on the list of options for the system files. 

Thank you very much! :D

And  I was planning something like this:

My drive is 500GB so, 
30 GB primary NTFS - Windows
30 GB primary Ext4 - / Ubuntu
235 GB Extended, logical, Ext4 /home
235 GB Logical NTFS  - Windows
5 GB - Swamp

What do you think? ...

---

### Post by amjjawad on 2010-12-24
> **Gforgio said:**
> Yeah, I read that windows mess up with everything if you install it later on, but I it seems its not that difficult to recover Ubuntu after all... I will try it that why, and yep, my question was whether for the Windows partition I should use the "do not use" option,  because the NTFS is not showed directly on the list of options for the system files. 

Thank you very much! :D

If you read my guides, you'll see that I always recommend the "Manual Installation" as it gives you more options and more control.

If you need anything, let us know :)

---

### Post by Zzl1xndd on 2010-12-24
+1 for amjjawad suggestion of using a Home Partition. Makes it a lot easier if anything goes belly up.

---

### Post by pricetech on 2010-12-24
I'd start with more than 30 gigs for each OS.  You'll probably want to do some experimenting, at least with Ubuntu, which will eat up quite a bit of space.

I'm also going to suggest you look into using Windows through a virtual machine such as VirtualBox.  Read up on that while you're doing your research and see if that meets your needs.  I'd at least set one up for the learning experience even if you dual boot.

Don't forget to back up your data on an external device in case of drive failure or the possible "oops".

---

### Post by Gforgio on 2010-12-24
> **pricetech said:**
> I'd start with more than 30 gigs for each OS.  You'll probably want to do some experimenting, at least with Ubuntu, which will eat up quite a bit of space.

I'm also going to suggest you look into using Windows through a virtual machine such as VirtualBox.  Read up on that while you're doing your research and see if that meets your needs.  I'd at least set one up for the learning experience even if you dual boot.

Don't forget to back up your data on an external device in case of drive failure or the possible "oops".

Thanks for the tips, the VirtualBox idea is a great idea. But what about the performance of windows 7 running in virtualbox, would it be much slower? or hardly any real difference? 

Thanks again.

---

### Post by Quackers on 2010-12-24
I have run 7 in Vbox and there is a performance hit but it is usable.

---

### Post by Gforgio on 2010-12-24
Thanks everyone, everything was very helpful!

---

### Post by amjjawad on 2010-12-24
> **Gforgio said:**
> Thanks everyone, everything was very helpful!

You welcome and if you have any other questions, please let us know :)

---

### Post by |Eric| on 2010-12-24
here is my usual scheme 
40gb windows
40gb linux 
512/1024 swap 
the rest is a data partition(either Fat32 /NTFs or EXt2  usualy ext2)
note that the ext2/3/4 driver dosent work well in vista and win7 
 
if i where you i would install windows first ( so much less trouble ) 
but if you dont want to install it right now just leave a "gap' of un-partitioned space for windows

use manual partitioning 
i usually go for ext2 but its more of a taste thing ... ext3-4 are fine as well for linux 

i don't do a /home partition because A- its gonna be full of system dependent settings and you can back it up anyway regardless 
B- its a waist as its not gona fill up much anyway  most ppl use their hdd for picture ,videos and music everything else is pretty minute in terms of space .

edit btw i dont use extended partitions

---

### Post by BeerFreek on 2011-01-21
Hi guys, sorry to bump in this thread


but I am planning to do a ubuntu install next weekend...

If I create the /home partition will it be "visible" to windows?  I wanted to keep all my Documents in one partition and be able to access it either OS I am atm....

So I was planning

/   with 60GB
Windows 60 GB
/home the rest of the space ( +/- 400GB ) 
/boot 300 MB
/swap 5000 MB

Is this possible ?

---

### Post by Elfy on 2011-01-21
If you want to access documents in both then use a windows file format.

60Gb for / is likely to be too much.

I'd not bother with /boot either unless you have specific reasons for doing so.

---

