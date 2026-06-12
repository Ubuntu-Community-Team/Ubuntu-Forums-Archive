---
title: "trying to install again"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by olmo47 on 2009-03-10
Ok! here it goes: The first time, I have try to install in my laptop, made mess out of it (problably my fult) here is what i got: I have a HP dv4t laptop with Vista, I would like to install this version of "ubuntu 7.10", (that I got some time back), I just learn how to made small pertition (no very proficient yet) in Vista, via small program that came with Vista.

Last time I have try to let Ubuntu do the partition and install,  made some problems for me.

Can some one "please", help me step by step, to have ubuntu as dual boot in a small pertition in my laptop?

Olmo47

---

### Post by Therion on 2009-03-10
Very good tutorial here with lots of screenshots:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by kansasnoob on 2009-03-10
Well, before we go any further, I should remind you that support for 7.10 ends in about one month!

---

### Post by kansasnoob on 2009-03-10
Also since one install failed it would be great to see what your partition scheme looks like.

So if you'd boot the live CD (choose to run without changes) and then go to System > Administration > Partition Editor and post a screenshot of the partition arrangement it would be lovely!

Even if you had to use Photobucket or something like that we'd appreciate it.

---

### Post by lavinog on 2009-03-10
May I recomend using 8.10 instead...it should work better. Also support for 7.04 will run out soon.

---

### Post by linux_lover69 on 2009-03-10
If you have trouble partitioning, you could always try wubi, and install it inside windows with no mess of repartitioning.

---

### Post by kansasnoob on 2009-03-10
> **lavinog said:**
> May I recomend using 8.10 instead...it should work better. Also support for 7.04 will run out soon.

Support for 7.04 ran out in October!

---

### Post by kansasnoob on 2009-03-10
> **linux_lover69 said:**
> If you have trouble partitioning, you could always try wubi, and install it inside windows with no mess of repartitioning.

Yuck! One power outage or "hard shutdown" and it's fried!

IMO, go for the dual boot!

---

### Post by linux_lover69 on 2009-03-10
> **kansasnoob said:**
> Yuck! One power outage or "hard shutdown" and it's fried!

IMO, go for the dual boot!

HAHA yeah, I was just giving out idea's

---

### Post by olmo47 on 2009-03-10
> **kansasnoob said:**
> Also since one install failed it would be great to see what your partition scheme looks like.

So if you'd boot the live CD (choose to run without changes) and then go to System > Administration > Partition Editor and post a screenshot of the partition arrangement it would be lovely!

Even if you had to use Photobucket or something like that we'd appreciate it.



Thanks for all the input, I feel overwelm by all the sugestions, some one said that this version will end soon, now i have to ask for other disc if any one will send me one?

---

### Post by olmo47 on 2009-03-10
> **kansasnoob said:**
> Support for 7.04 ran out in October!

yes some one in the forum send me this version! perhaps will be best to get a newer version?

---

### Post by kansasnoob on 2009-03-10
What are your hardware specs?

---

### Post by olmo47 on 2009-03-10
> **lavinog said:**
> May I recomend using 8.10 instead...it should work better. Also support for 7.04 will run out soon.

I am no sure (or remember) ware I need to go to ask for another CD?
sugestions are welcom?

---

### Post by linux_lover69 on 2009-03-10
Did you try going to ubuntu.com and request a CD?

---

### Post by burnetbj on 2009-03-10
Just my opinion here but I started on 6.** cant remember and it was hard to under stand and to get things to work was a crazy chore. 7.** was a great improvement, then 8.** came along and I was amazed at the progress these programmers are capable of making in such a short time. I would recommend a new user start with the latest as they have the ease of use in mind and seem to be actually easier to use. 

If you run into if you run into hardware issue dont panic ask questions......someone here has always been able to help me out of it.....

If that doesnt work, try another version and all beginers should start with 32 bit....just less gotchas out there. 

Again just my opinion

---

### Post by olmo47 on 2009-03-10
> **kansasnoob said:**
> What are your hardware specs?

You mean what inside my laptop?

2.6hg T9400 / 4gb ram / 250gb HD / NVIDIA Geforce 9200M GS

will that help?

---

### Post by olmo47 on 2009-03-10
> **burnetbj said:**
> Just my opinion here but I started on 6.** cant remember and it was hard to under stand and to get things to work was a crazy chore. 7.** was a great improvement, then 8.** came along and I was amazed at the progress these programmers are capable of making in such a short time. I would recommend a new user start with the latest as they have the ease of use in mind and seem to be actually easier to use. 

If you run into if you run into hardware issue dont panic ask questions......someone here has always been able to help me out of it.....

If that doesnt work, try another version and all beginers should start with 32 bit....just less gotchas out there. 

Again just my opinion

Thanks
I think I will try to get 8.04 some one sugested that version. not sure ware to ask for?

---

### Post by olmo47 on 2009-03-10
> **linux_lover69 said:**
> Did you try going to ubuntu.com and request a CD?

No yet thanks I need to search to find that page.:D

---

### Post by lavinog on 2009-03-10
> **olmo47 said:**
> Thanks
I think I will try to get 8.04 some one sugested that version. not sure ware to ask for?

go for 8.10, you might have less problems
also you can download the cd or request a free cd here:
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

---

### Post by burnetbj on 2009-03-10
Ok i read through all the other post, you dont need to wait or send for another CD you can upgrade after you get installed. I wouldnt go for the wubi install. Just partition the Hard Drive in half leaving both sides equal in size allowing plenty of room to increase or decrease in size.

Once you get the partition completed incert CD and reboot while BIOS is set to boot from CD first. Once you boot you will receive a prompt to boot in safe graphics mode (choose this) once you have the LiveCD running and it looks like its installed you will see a icon called (install) choose this. 

This will take you through a Graphical install and allow you to choose 3 types of installs. You can choose either a custom install which if you go this route i would suggest 5Gb root or \ symbole, then they say one and a half times your RAM size for Swap but since your at 4 Gb RAM and just trying all this out in sure 2Gb OK .....might want to get a sec opinion on this part. Then the remaining free space for HOME partition.

Or you could just choose install on largest remaining free space and the Installer will complete this for you. My two bits anyhow

---

### Post by olmo47 on 2009-03-10
> **olmo47 said:**
> Ok! here it goes: The first time, I have try to install in my laptop, made mess out of it (problably my fult) here is what i got: I have a HP dv4t laptop with Vista, I would like to install this version of "ubuntu 7.10", (that I got some time back), I just learn how to made small pertition (no very proficient yet) in Vista, via small program that came with Vista.

Last time I have try to let Ubuntu do the partition and install,  made some problems for me.

Can some one "please", help me step by step, to have ubuntu as dual boot in a small pertition in my laptop?

Olmo47
------------------------------------------

I am geting the new version, will take 2hr.

Thanks for all your help.

I will post or ask for help when all is done.

olmo47 :)

---

### Post by kansasnoob on 2009-03-10
> **olmo47 said:**
> ------------------------------------------

I am geting the new version, will take 2hr.

Thanks for all your help.

I will post or ask for help when all is done.

olmo47 :)

I'd love to know what your drive looks like right now since you had one failed install!!!!!!!!!!!

Very important!

Also IMHO Vista's partitions should only be resized using Vista's own tools! I know not everyone agrees with that but I've spent too many hours fiddling around after resizing Vista partitions with Gparted!

---

### Post by olmo47 on 2009-03-11
> **kansasnoob said:**
> I'd love to know what your drive looks like right now since you had one failed install!!!!!!!!!!!

Very important!

Also IMHO Vista's partitions should only be resized using Vista's own tools! I know not everyone agrees with that but I've spent too many hours fiddling around after resizing Vista partitions with Gparted!

OK I have download the new version, I will try to partition vista with the little partition tool that came with.

I will burn it on a CD-R? or DVD+? or aby sugestions?

---

### Post by bailbath on 2009-03-11
Burn to a cd. 

Here is the link that was gave to earlier
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Ian

---

### Post by olmo47 on 2009-03-19
> **kansasnoob said:**
> I'd love to know what your drive looks like right now since you had one failed install!!!!!!!!!!!

Very important!

Also IMHO Vista's partitions should only be resized using Vista's own tools! I know not everyone agrees with that but I've spent too many hours fiddling around after resizing Vista partitions with Gparted!



Help I need please:Ok I got the new version put it on a CD now I have this other problem not sure how to start?

My system has crash badly, I had to clean the computer (all of the files) I have to put my computer to original factory specs, so I have install to Vista OS, now (after install what I need it) I have left 174 GB, however, I try to reinstall Ubuntu.
I went to, the little program that comes with Vista, to get a 20 GB partition, and this is what I have available:

Computer Management, under Storage/Disk Management/ Shrink Volume that I only have &#8220;467 MB&#8221; for shrinking "Total size before shrink in MB 228088" but I went to properties it show me that I have available free 174.432.886.784 (164 GB).

I have defragmented 3 times correct the error (if any) and went back to try again and have the same amount.

Any suggestions, as to get 20 GB out of the 164 GB to reinstall Ubuntu again?

My Laptop came 250 GB I have a partition for the buck up original files, the Disk management shows both petition (C) 222.74 GB NTFS / HP Recovery (D) 10.14 GB NTFS.

---

### Post by lavinog on 2009-03-20
I didn't know vista would let you shrink partitions. I always use gparted on the ubuntu live cd. It's pretty easy.

---

