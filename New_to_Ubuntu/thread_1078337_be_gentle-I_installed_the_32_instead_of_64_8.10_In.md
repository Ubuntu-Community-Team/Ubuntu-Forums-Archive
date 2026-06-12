---
title: "be gentle-I installed the 32 instead of 64 8.10 Intrepid ibex"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by annie22 on 2009-02-23
I am absolutely knew,today,to ubuntu which I've desired for a long time and have taken the plunge.I had 2 disks arrive today-intrepid ibex 64 and the 32bit 8.10.
I've stupidly installed the 32 when I realised I have a 64 system and the extra disk of goodies comes with the 64.
my question is how do I uninstall to put the intrepid ibex(64) on?
Even the installation is very different and I'm not a code type person.
I want to get rid eventually of xp(asap) and have it set as dual boot for the moment and would rather not have to reformat my C:drive AT ALL(until I'm competent enough i.e).
Thankyou and I'm very happy to be here at last!;)

---

### Post by ibizatunes on 2009-02-23
You have to reinstall x64 from scatch, there is everything in x32 that is in ubuntu x64
But if you have a x64 processor install the x64 version is my recommendation

---

### Post by TenPlus1 on 2009-02-23
If the 32-bit edition is working fine then why not use that instead...

If unfortunately you need access to more than 3gb of memory or use specific high-processing-power apps then re-install 64-bit...

---

### Post by The Cog on 2009-02-23
You may as well continue with the 32 bit unless there's a good reason to change. If you do, probably the easiest way is to use XP to delete the two extra partitions that Ubuntu put on there. Then you can just use the installer option to use the free space. Or you can use the live CD to remove the extra partitions - System > Administration > Partition Editor. Note that until you install the other Ubuntu, XP will be unbootable because the GRUB bootloader relies on files in the deleted Ubuntu partition.

---

### Post by annie22 on 2009-03-12
> **TenPlus1 said:**
> If the 32-bit edition is working fine then why not use that instead...

If unfortunately you need access to more than 3gb of memory or use specific high-processing-power apps then re-install 64-bit...

Thankyou,2 weeks later after my D-500g sata died(my C drive is IDE,160g),I've finally got my computer back with XP Pro installed and I'm nervously preparing to have another go.
My very first 8.10 install went perfectly btw,malware in xp I think coincided with my HD's demise.I'm thinking of using the 32bit as Tenplus1's suggested.Been reading forum etc.
I'm so,so new to this I admit I do not understand much of the lingo.I need EASY:) until I'm familiar enough and I presume it'll be like my late intro to windows,I'll get there.

---

### Post by annie22 on 2009-03-12
I agree-as with the other replies you'll see I had a HD failure which put everything on hold.I will be installing the 8.10 32bit desktop edition I received from Ubuntu.
Thankyou

---

### Post by philinux on 2009-03-12
If you got a 64 bit pc then install the 64 bit OS. No brainer :lolflag:

Everything work in 64 bit now. No problemo.

---

### Post by presence1960 on 2009-03-12
Just go ahead and install the 64bit. When you get to the partitioner choose manual and install the 64 bit to the partition(s) on which the 32 bit is installed. If that worries you, you can use the CD to run gparted and format the linux partition(s). Then do the install and use manual on the partitioner. When you reinstall to the linux partition(s) grub will be reinstalled and should contain an entry for windows since it looks for other OS's during installation.

---

### Post by annie22 on 2009-03-26
> **philinux said:**
> If you got a 64 bit pc then install the 64 bit OS. No brainer :lolflag:

Everything work in 64 bit now. No problemo.

Thanks Phil,the thing is the 64 wouldn't begin to install.
I've now put XP home on and used wubi to install the 32(until I'm confident enough to turf MS for good-hope).
It's odd,perhaps something's wrong with the disk(64) though the inspection said it was fine.At least I'm away on my voyage at last

---

