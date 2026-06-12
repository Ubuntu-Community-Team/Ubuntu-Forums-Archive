---
title: "swap"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by lanceps on 2009-05-13
my friend told me i have to make 1 GB swap partetion when i am installing linux, is it necessary and why am i making it. 

can i use that memory to store files

---

### Post by Didius Falco on 2009-05-13
A swap file is what is used when your memory is full - it's treated like extra (but much slower) RAM. It would also be used if you were putting your PC into Hibernation Mode.

You can't store files in it like you can in a regular directory. It's for the system to use.

How much Ram is in your PC?

---

### Post by lanceps on 2009-05-13
768 MB( 256 +512) is it necessary to make it i only got 10GB that i can use so giving one gb is a lot

---

### Post by lanceps on 2009-05-13
anyone pls help

---

### Post by Didius Falco on 2009-05-13
You are going to be a little cramped for space with only 10 gigs to use. You could make a 400-500 Meg swap file.

If you are using more swap than that, your pc is going to crawling anyway. You'll just have to try and not load too much up at one time as far as games or huge graphics, etc.

Regards,

Didius

---

### Post by louieb on 2009-05-13
If you plan to hibernate the computer you must have swap at least as large as the amount of ram. 

If you don't hibernate the computer then you can do without a swap partition. On computers I don't hibernate I make a 1/4 - 1/2 GB swap partition.  With 3/4 GB ram and not much disk space I'd make a small swap partition.

In windows its called virtual memory, in Linux its swap. Same thing different name.

---

### Post by Sir Jasper on 2009-05-13
Hi,

This is for infomation:

I have 640 MB RAM and a 500 MB swap partition.
I don't ever use hibernation. 

I have yet to use more than a mere 5 MB of swap.

I usually turn it off with sudo swapoff /dev/sdb5 
the final "sdb5" is specific for me.

You could change the sizes of your partitions using Gparted.

I think, you could try a swap file rather than a swap pertition.

I'm not an expert and I have no idea what resources you may
need for your computing habits, so I'm happy to try to help but
without giving advice.

My regards

---

### Post by billgoldberg on 2009-05-13
You don't have to use swap if you don't like. But that can give problems with only 7xxmb of ram.

You could always make a swap file instead of partition 1gb for it.

See here for instructions:
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by mcduck on 2009-05-13
> **lanceps said:**
> 768 MB( 256 +512) is it necessary to make it i only got 10GB that i can use so giving one gb is a lot

With less than 1GB of RAM, you are quite likely to really need the swap if you are going to use the machine for any other than most basic tasks. I'd recommend making 1GB swap partition, even more would be better but with hard disk that small you probably want to have as much disk space as possible for your own use..

Here's my basic rules for swap:

Less than 1GB RAM: at least 1GB swap.
More than 1GB RAM, suspend: swap the same size your RAM is.
More than 1GB RAM, no suspend: 1GB swap.

---

### Post by Sir Jasper on 2009-05-13
Hi again,

Well, as I said I have no idea about your computing habits.

I used Gparted to reduce the size of my swap file by some two thirds, so you could reduce yours if you follow mcduck's advice with 1GB setting and that tranapires to be too much. With 10 GB in total any sizing adjustments should be reasonably quick.

Certainly mcduck was a great help to me a couple of months ago and I'm sure all your advisers know a lot more than I do.

Perhaps, with proper advice, you could put a fastish USB 2 flash drive to work if you run short of space?

I never do more than three things at once e.g. play music, backup in the background and browse with Firefox but I don't ever play games, all deleted,
or use "heavy" graphics programs. 

My regards

---

