---
title: "i want to erase a partition"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by jsf_pp on 2009-01-15
hi, im trying to erase a partition with GParted from a CD live (ubuntu 8.10). thing is i can't. i did right clic on it to get the option's list but i only have access to:

-new
-
-
-
-
-
-
-information

so, can you help me?
thanks!

---

### Post by minsf on 2009-01-15
Please open a terminal (Applications > Accesories >Terminal), enter ```
sudo fdisk -l
``` and post the output here, so that we have a better idea of how your current partitions look like. otherwise, please post a snapshot of the gparted. 
by the way, are you sure all partitions are unmounted?
are you clicking an unallocated space?

---

### Post by jsf_pp on 2009-01-15
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0c74625

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

```

im not sure if its unmounted, how can i know that? im uploading a screenshot right now.

[[IMG]http://img218.imageshack.us/img218/2940/65729847sc2.th.png[/IMG]](http://img218.imageshack.us/my.php?image=65729847sc2.png)

---

### Post by jsf_pp on 2009-01-15
help.:)

---

### Post by sdowney717 on 2009-01-15
right click sda1 in the list and it should show you a bunch of options

---

### Post by jsf_pp on 2009-01-15
sdowney747: but i want to erase the other one, not sda1.

so i right clic it and:

[IMG]http://i42.tinypic.com/35dds3d.png[/IMG]

---

### Post by sdowney717 on 2009-01-15
you are clicking on unallocated space, that means it is not partitioned yet

so then you can partition it using "new"

But it is so small.

What are you trying to do with this small space?

---

### Post by jsf_pp on 2009-01-15
> **sdowney717 said:**
> you are clicking on unallocated space, that means it is not partitioned yet

so then you can partition it using "new"

But it is so small.

What are you trying to do with this small space?

im just trying to erase it. my laptop came with this kind of security restoration system on it, which takes you to VISTA. but i already erased VISTA long time ago so its just taking space uselessly (im not sure if that word exists actually... heheh).

anyway, i want to erase it in order to have those 7 gb back. thing is i want to install ubuntu again cuz i was using wubi and im kind of sick of windows. im taking the BIG step here. but i want to have the whooooole disk for my personal leisure.

hey, thanks for staying with me dude!

---

### Post by oldos2er on 2009-01-15
It's 7MB, not 7GB, and you can't "erase" hard disk space. Have you tried expanding sda1 to include that space?

---

### Post by jsf_pp on 2009-01-15
> **oldos2er said:**
> It's 7MB, not 7GB, and you can't "erase" hard disk space. Have you tried expanding sda1 to include that space?

OMG!!! you are totally right! im sooo stupid-blinded. anyway, this is an 80 gb hard disk. so where are my 5.48 Gb left?

you see, thats why im asking, cuz when my laptop starts i get this screen of the company's name eventhough i already did format c: on wintendo.

im just trying to get those 5.48 gb back. but it seems even gparted cant see it.

i went to the store where i bought this laptop and they told me it was a *in english would be like* phantom partition. (ghost partition, dunno)

thanks for your hel guys!

---

### Post by jsf_pp on 2009-01-15
> **oldos2er said:**
>  Have you tried expanding sda1 to include that space?

no risk doin it? i'll do it then right now.

---

### Post by estyles on 2009-01-15
The company's name/splash screen are stored in the BIOS.  You can't really get rid of it without flashing the BIOS, and don't do that.

You aren't really missing 5 GB of disk space.  What is missing is truth in advertising.  What hard drive manufacturers call a gigabyte is 1,000,000,000 bytes.  Which is really only .93 GB.  So an 80 GB hard drive is only about 74.5 GiB (where GiB stands for what should be the correct definition of a gigabyte, which is 1024 megabytes, which in turn should be 1024 kilobytes, which in turn is 1024 bytes).  A GB should theoretically be 1,073,741,824 bytes, but according to HD manufacturers, it's not.

---

### Post by minsf on 2009-01-15
jsf, you have an NTFS file system on 99.9% of your partition. the rest of the space is not yet "defined"
> **jsf_pp said:**
> im just trying to erase it
it is not used at all, so you obviously dont have the option to erase something that doesnt exist yet :)
> **jsf_pp said:**
> my laptop came with this kind of security restoration system on it, which takes you to VISTA. but i already erased VISTA long time ago so its just taking space useless.
maybe in the past you had this security feature that backs up your data to another partition, BUT NOT ANYMORE, according to your current partition tables.
> **jsf_pp said:**
> anyway, i want to erase it in order to have those 7 gb back.
please notice the unallocated space is very very small- about 7 to 11 MB, not GB.
> **jsf_pp said:**
> 
thing is i want to install ubuntu again cuz i was using wubi and im kind of sick of windows. im taking the BIG step here. but i want to have the whooooole disk for my personal leisure.
So when installing ubuntu from a live cd, chose to install it on the entire disk. then all the space will be used for ubuntu. (by default, ubuntu will try to shrink the windows, and install itself to the side of windows partition. when it asks you to confirm, during the installation preocess, (after selecting the region and langauge, i think) you have to change this default setting to intalling on the entire disk (i think it's the last of the three options) and only then confirm. DONT FORGET TO BACK UP your date before you do this.

---

### Post by jsf_pp on 2009-01-15
> **estyles said:**
> The company's name/splash screen are stored in the BIOS.  You can't really get rid of it without flashing the BIOS, and don't do that.

You aren't really missing 5 GB of disk space.  What is missing is truth in advertising.  What hard drive manufacturers call a gigabyte is 1,000,000,000 bytes.  Which is really only .93 GB.  So an 80 GB hard drive is only about 74.5 GiB (where GiB stands for what should be the correct definition of a gigabyte, which is 1024 megabytes, which in turn should be 1024 kilobytes, which in turn is 1024 bytes).  A GB should theoretically be 1,073,741,824 bytes, but according to HD manufacturers, it's not.

now you tell me where is the thank-you-so-fuck1n-much-button and i'll press it right away.

thanks. really. sorry if i made you guys lose your time. really.
and this is another PRETTY-MUCH-SOLVED thread!!!

THANKS! 
:guitar:

---

### Post by oldos2er on 2009-01-15
> **jsf_pp said:**
> no risk doin it? i'll do it then right now.

 There's always risk of data loss when one manipulates partitions; hopefully you have or can make backups.

---

### Post by estyles on 2009-01-15
> **jsf_pp said:**
> now you tell me where is the thank-you-so-fuck1n-much-button and i'll press it right away.

thanks. really. sorry if i made you guys lose your time. really.
and this is another PRETTY-MUCH-SOLVED thread!!!

THANKS! 
:guitar:

hehe.  They disabled thanks and some other features for the time being while they wait for new hardware or something like that.

And yeah, the "missing" harddrive space on drives that are advertised to be "N" gigabytes is annoying.  My 1 TB drive is just over .9 TiB in reality.  And the bigger the modifier, the more incorrect the advertised capacity is.

---

### Post by jsf_pp on 2009-01-15
> **minsf said:**
> jsf, you have an NTFS file system on 99.9% of your partition. the rest of the space is not yet "defined"

it is not used at all, so you obviously dont have the option to erase something that doesnt exist yet :)

maybe in the past you had this security feature that backs up your data to another partition, BUT NOT ANYMORE, according to your current partition tables.

please notice the unallocated space is very very small- about 7 to 11 MB, not GB.

So when installing ubuntu from a live cd, chose to install it on the entire disk. then all the space will be used for ubuntu. (by default, ubuntu will try to shrink the windows, and install itself to the side of windows partition. when it asks you to confirm, during the installation preocess, (after selecting the region and langauge, i think) you have to change this default setting to intalling on the entire disk (i think it's the last of the three options) and only then confirm. DONT FORGET TO BACK UP your date before you do this.

thanks dude, this is really useful information. i'll be backing up for the next hours. i hope by night time i have my KICKIN A*S*S UBUNTU runnin

---

### Post by jsf_pp on 2009-01-15
> **estyles said:**
> hehe.  They disabled thanks and some other features for the time being while they wait for new hardware or something like that.

And yeah, the "missing" harddrive space on drives that are advertised to be "N" gigabytes is annoying.  My 1 TB drive is just over .9 TiB in reality.  And the bigger the modifier, the more incorrect the advertised capacity is.

i hope in the few next years, as GB will turn up into TB, more ppl realize about this issue just like i did 2 minutes ago and hardware advertising change this fraud-way-to-f*u*c*k-us-up.

---

### Post by estyles on 2009-01-15
> **jsf_pp said:**
> i hope in the few next years, as GB will turn up into TB, more ppl realize about this issue just like i did 2 minutes ago and hardware advertising change this fraud-way-to-f*u*c*k-us-up.

Heh, unlikely.  It has basically been decided by the industry that GiB (gibibyte?) and TiB (tebibyte?) will be used to denote the true, "proper" size gigabyte and terabyte.  While GB and TB are basically ambiguous.  Those who want to use TiB and GiB intend for GB and TB to be 1,000,000,000 and 1,000,000,000,000 bytes respectively, but people still use GB and TB to represent what *I* and many feel are "proper" sized gigabytes and terabytes, using 2^10 instead of 10^3 as the multiplicative factor.  And so, it's hard to know for sure what GB and TB mean.  Assume when buying harddrives that the manufacturers use the term that makes their drives look bigger, i.e. 10^3 sized jumps.

---

### Post by Lupy on 2009-01-15
So what  they advertise as a Gigabyte is really only a Gigibyte? That seems like false advertising to me... :mad:

---

### Post by jsf_pp on 2009-01-15
just look what i-ve found... [http://forum.utorrent.com/viewtopic.php?id=2154](http://forum.utorrent.com/viewtopic.php?id=2154)

the same thing. SPREAD THE WORD! hahah, no, really. let's spread the word guys, no case explainin to my mom but im sure some ppl out there would like to know they are being cheated.

---

