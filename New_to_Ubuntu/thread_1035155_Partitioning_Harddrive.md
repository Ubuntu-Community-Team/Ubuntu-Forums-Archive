---
title: "Partitioning Harddrive"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Wovaki on 2009-01-09
Hello!

I have recently been using Ubuntu 8.10 with a Wubi install, and I think I would like to go ahead and partition my hard drive, with a dual-boot, but I have a few questions I would like to ask first.

**1. I am running Vista, will using the LiveCD to partition my drive, with a dual-boot, work fine on Windows Vista?**
I heard that its not completely compatible with Vista yet.

**2. How much hard drive space should I give my Ubuntu boot?**
This will be my first time partitioning a hard drive, and I'm not exactly sure how everything works.

**3. I know I should backup everything first, but partitioning my drive should keep all my windows files and stuff untouched, right?**

Thanks for the help!
Wovaki

---

### Post by thegreenblob on 2009-01-09
1: Last week I installed ubuntu on my friends PC with Vista and it worked just fine with a dual boot.

2: I would say give ubuntu at least 10GB. But preferably more. :P

3: Yeah, all your files should be fine. But there's always a risk when partitioning so back them up just in case. (But in my experience I have never lost data do to partitioning)

---

### Post by jsroth on 2009-01-09
This worked fine for me:
I repartitioned my harddisk in Windows in such a way that I had one partition for Windows and one for Linux.

Then, using the Ubuntu installer, I repartitioned the one partition I had for Linux into one ext3 which is mounted as /boot (should have something like 200 MB) another ext3 for the / file system (around 10 GB), then I have 2 GB as swap (should be same as your RAM size I think) and the rest is again ext3 mounted as /home

Like this my Windows partition remained untouched and Ubuntu installed GRUB perfectly making dual-booting perfectly possible :)

---

### Post by cecure on 2009-01-09
One word of advice, I would defrag your windows partition first... just to be safe

---

### Post by Wovaki on 2009-01-09
> **thegreenblob said:**
> 1: Last week I installed ubuntu on my friends PC with Vista and it worked just fine with a dual boot.

2: I would say give ubuntu at least 10GB. But preferably more. :P

3: Yeah, all your files should be fine. But there's always a risk when partitioning so back them up just in case. (But in my experience I have never lost data do to partitioning)

That 10GB would be like the size of your "Linux Hard Drive" right? So I could only store 10GB of data on my Linux boot if I give it 10GB?

> **jsroth said:**
> This worked fine for me:
I repartitioned my harddisk in Windows in such a way that I had one partition for Windows and one for Linux.

Then, using the Ubuntu installer, I repartitioned the one partition I had for Linux into one ext3 which is mounted as /boot (should have something like 200 MB) another ext3 for the / file system (around 10 GB), then I have 2 GB as swap (should be same as your RAM size I think) and the rest is again ext3 mounted as /home

Like this my Windows partition remained untouched and Ubuntu installed GRUB perfectly making dual-booting perfectly possible :)

This I don't understand... Does this mean that when the HDD is partitioned it is going to make 3 different partitions?
Its confusing to me, could you please explain it a little, or show me where I can read up on this stuff?

Thanks

> **cecure said:**
> One word of advice, I would defrag your windows partition first... just to be safe

Yeah, I will defrag before I do anything.

Thanks.

---

### Post by thegreenblob on 2009-01-09
> **Wovaki said:**
> That 10GB would be like the size of your "Linux Hard Drive" right? So I could only store 10GB of data on my Linux boot if I give it 10GB?



This I don't understand... Does this mean that when the HDD is partitioned it is going to make 3 different partitions?
Its confusing to me, could you please explain it a little, or show me where I can read up on this stuff?

Thanks

Yeah. I was talking about 10GB (at least) for the whole system. And by default Ubuntu will only make 2 partitions a / and a swap. Which the installer will configure both of these automatically for you once you choose how much space you want ubuntu to have. I believe he thought you were going to partition ubuntu manually in which case you can set it up how ever you like. :)

---

### Post by Wovaki on 2009-01-09
> **thegreenblob said:**
> Yeah. I was talking about 10GB (at least) for the whole system. And by default Ubuntu will only make 2 partitions a / and a swap. Which the installer will configure both of these automatically for you once you choose how much space you want ubuntu to have. I believe he thought you were going to partition ubuntu manually in which case you can set it up how ever you like. :)

Like I said before, this will be my first time ever partitioning anything. So I am planning just to use the LiveCD, since it seems that people are not having problems with it on Vista.

So I will probably want more than 10GB for my Ubuntu boot, so I can have enough room for music and videos and stuff like that. My computers HDD is over 200GB (I'm not sure on exact size, I'm at school right now) and I think I have over 100GB free space.

Whats the difference between the two partitions ("/" and "swap") and which one is it that has something to do with my RAM (which is about 3GB I think)

Also, when I go to install, all I will have to do for partitioning it (with the LiveCD) is choose the size of the "/" and "swap" partitions?

Thanks!
Wovaki

---

### Post by thegreenblob on 2009-01-09
> **Wovaki said:**
> Like I said before, this will be my first time ever partitioning anything. So I am planning just to use the LiveCD, since it seems that people are not having problems with it on Vista.

So I will probably want more than 10GB for my Ubuntu boot, so I can have enough room for music and videos and stuff like that. My computers HDD is over 200GB (I'm not sure on exact size, I'm at school right now) and I think I have over 100GB free space.

Whats the difference between the two partitions ("/" and "swap") and which one is it that has something to do with my RAM (which is about 3GB I think)

Also, when I go to install, all I will have to do for partitioning it (with the LiveCD) is choose the size of the "/" and "swap" partitions?

Thanks!
Wovaki

Ah. Well if you have that big of an HD then yeah, you'll probably want something way bigger than 10GB :P

And / is where the operating system, all the programs, and your data will go. The swap is just what the system uses as a backup in case you run out of ram.

And you don't really have to choose the size of both, just during the installer there's an option "Guided - Resize IDE Master" (or something like that), and then you choose how much space you want windows to have and how much space you want ubuntu to have. It will auto configure the size of the swap and / for you after that. (/ will be big, and swap will be a small portion)

---

### Post by Wovaki on 2009-01-09
> **thegreenblob said:**
> Ah. Well if you have that big of an HD then yeah, you'll probably want something way bigger than 10GB :P

And / is where the operating system, all the programs, and your data will go. The swap is just what the system uses as a backup in case you run out of ram.

And you don't really have to choose the size of both, just during the installer there's an option "Guided - Resize IDE Master" (or something like that), and then you choose how much space you want windows to have and how much space you want ubuntu to have. It will auto configure the size of the swap and / for you after that. (/ will be big, and swap will be a small portion)

Alright thanks!

So how much room should I give to my Ubuntu boot?

Or should I go with the "Guided - Resize IDE Master"?

Thanks!

---

### Post by thegreenblob on 2009-01-09
Yeah, I would go with the resize option as it's generally easier than anything else to dual boot.

And I personally would probably give Ubuntu 100GB out of the 200GB. :)

Hope this helps.

---

### Post by Dedoimedo on 2009-01-09
> **Wovaki said:**
> Hello!

I have recently been using Ubuntu 8.10 with a Wubi install, and I think I would like to go ahead and partition my hard drive, with a dual-boot, but I have a few questions I would like to ask first.

**1. I am running Vista, will using the LiveCD to partition my drive, with a dual-boot, work fine on Windows Vista?**
I heard that its not completely compatible with Vista yet.

**2. How much hard drive space should I give my Ubuntu boot?**
This will be my first time partitioning a hard drive, and I'm not exactly sure how everything works.

**3. I know I should backup everything first, but partitioning my drive should keep all my windows files and stuff untouched, right?**

Thanks for the help!
Wovaki

Hi there,

1) Maybe. It "should" be ok, but there's always a chance for problems.
2) Ubuntu will need only a handful of GB, but if you want it to grow and run lots of apps and save lots of data, you'll need quite a bit of space. If you can afford it: 16GB root, 2GB swap, and 32GB home. That's a total 50GB. Good enough for first impressions and testing. But you can go as low as 4GB.
3) Maybe. It depends what you do with your partitioning. I warmly recommend: backup, backup, backup!

Dedoimedo

---

### Post by Wovaki on 2009-01-09
> **thegreenblob said:**
> Yeah, I would go with the resize option as it's generally easier than anything else to dual boot.

And I personally would probably give Ubuntu 100GB out of the 200GB. :)

Hope this helps.

The "Guided" one?
And if I have only 100GB free on my Windows Boot, and give 100GB to my Ubuntu Boot, does that mean I will have 0GB free space on Windows?

Thanks!

---

### Post by thegreenblob on 2009-01-09
> **Wovaki said:**
> The "Guided" one?
And if I have only 100GB free on my Windows Boot, and give 100GB to my Ubuntu Boot, does that mean I will have 0GB free space on Windows?

Thanks!

Yeah the guided - resize one. (There's actually more than one guided option, just remember to choose the resize one cause the guided - use entire disk would delete windows and then install ubuntu) :P

And yeah if ALL you have is 100GB left in windows and you give ubuntu 100GB it would leave 0GB left. So maybe go a little smaller. :)

---

### Post by Wovaki on 2009-01-09
> **Dedoimedo said:**
> Hi there,

1) Maybe. It "should" be ok, but there's always a chance for problems.
2) Ubuntu will need only a handful of GB, but if you want it to grow and run lots of apps and save lots of data, you'll need quite a bit of space. If you can afford it: 16GB root, 2GB swap, and 32GB home. That's a total 50GB. Good enough for first impressions and testing. But you can go as low as 4GB.
3) Maybe. It depends what you do with your partitioning. I warmly recommend: backup, backup, backup!

Dedoimedo

I don't understand how I would specify certain amounts of space for each swap? I thought there was only two options here?

I'm going to use the LiveCD to do it, since I don't know anything about partitioning.

What if I give it 50GB, then decide later on I want 100GB...do I have to repartition and reinstall Ubuntu?

Thanks!

---

### Post by thegreenblob on 2009-01-09
> What if I give it 50GB, then decide later on I want 100GB...do I have to repartition and reinstall Ubuntu?

Yeah, you can resize it later if you want to using the gparted live cd.

---

### Post by Wovaki on 2009-01-09
> **thegreenblob said:**
> Yeah the guided - resize one. (There's actually more than one guided option, just remember to choose the resize one cause the guided - use entire disk would delete windows and then install ubuntu) :P

And yeah if ALL you have is 100GB left in windows and you give ubuntu 100GB it would leave 0GB left. So maybe go a little smaller. :)

Alright, maybe I will give it 50 or 75GB or something then.

Thanks for your help, you have really made this alot easier for me!
Wovaki

---

### Post by Wovaki on 2009-01-09
> **thegreenblob said:**
> Yeah, you can resize it later if you want to using the gparted live cd.

Whats the gparted Live cd?
or is that just the normal LiveCD that I install from?

And if I resize, is it going to leave my Windows and Ubuntu files intact.

@offtopic
Does anyone know how you actually pronounce Ubuntu?

Thanks!

---

### Post by Dedoimedo on 2009-01-09
Hi,

swap refers to a part of harddisk reserved for memory swapping when real memory gets low.

You can choose the size for each partition if you select the custom option.

Please see here:
[http://www.dedoimedo.com/computers/install_kubuntu.html](http://www.dedoimedo.com/computers/install_kubuntu.html)
[http://www.dedoimedo.com/computers/dual_boot.html](http://www.dedoimedo.com/computers/dual_boot.html)

Cheers,
Dedoimedo

---

### Post by thegreenblob on 2009-01-09
> **Wovaki said:**
> Whats the gparted Live cd?
or is that just the normal LiveCD that I install from?

And if I resize, is it going to leave my Windows and Ubuntu files intact.

@offtopic
Does anyone know how you actually pronounce Ubuntu?

Thanks!

The gparted live cd is just a cd that you boot from (much like the ubuntu live cd), except it's specifically for partitioning. 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

So you could resize your partitions that way later if you wanted.

---

### Post by Wovaki on 2009-01-09
> **Dedoimedo said:**
> Hi,

swap refers to a part of harddisk reserved for memory swapping when real memory gets low.

You can choose the size for each partition if you select the custom option.

Please see here:
[http://www.dedoimedo.com/computers/install_kubuntu.html](http://www.dedoimedo.com/computers/install_kubuntu.html)
[http://www.dedoimedo.com/computers/dual_boot.html](http://www.dedoimedo.com/computers/dual_boot.html)

Cheers,
Dedoimedo

Thanks, but since I'm new to this wouldn't it be better for me to use the "Guided" partition thing thegreenblob mentioned before?

> **thegreenblob said:**
> The gparted live cd is just a cd that you boot from (much like the ubuntu live cd), except it's specifically for partitioning. 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

So you could resize your partitions that way later if you wanted.

Thanks, I appreciate all your help!

---

### Post by -kg- on 2009-01-09
You can also find a bit of good information in the ["How To Partition"]("https://help.ubuntu.com/community/HowtoPartition") section of the Ubuntu Community Documentation.  This page is only on partitioning...other pages in the Documentation will contain a lot of good information on other areas of the installation/usage of Ubuntu Linux.

:D

---

