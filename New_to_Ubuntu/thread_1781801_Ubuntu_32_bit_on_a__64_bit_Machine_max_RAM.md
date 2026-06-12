---
title: "Ubuntu 32 bit on a  64 bit Machine max RAM"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by rvgsd on 2011-06-14
Hi, I wanted to know how much RAM can a 32 bit Ubuntu installation recognize, if its running on a 64 bit machine/processor using a PAE kernel.
I have searched online and found that it can support upto 8GN ([http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)), But I just wanted to confirm with you guys before spending money and upgrading from 4 to 8 GB.
(I don't want to go for a 64 bit installation!)
Thanks for the help.

---

### Post by wildmanne39 on 2011-06-14
> **rvgsd said:**
> Hi, I wanted to know how much RAM can a 32 bit Ubuntu installation recognize, if its running on a 64 bit machine/processor using a PAE kernel.
I have searched online and found that it can support upto 8GN ([http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)), But I just wanted to confirm with you guys before spending money and upgrading from 4 to 8 GB.
(I don't want to go for a 64 bit installation!)
Thanks for the help.
Hi, use a pae kernel it can use more then four for sure but I am not sure it can use 8, I have been using 64 bit for 4 years without any problems and it runs just a little faster then 32 bit.

---

### Post by vkbidve on 2011-06-14
A 32 bit system can address upto 2^32 = 4 GB RAM only. 

If you want higher amount of ram, then go with 64 bit system (hardware and software as well). There are millions of 64 bit systems running happily out there. No problem in using 64 bit system.

---

### Post by 3rdalbum on 2011-06-14
The PAE kernel uses 36-bit addressing, which gives you 64 GiB of addressable RAM. However, it's all up to your motherboard to support the 8 GiB of RAM.

I really don't know why you wouldn't just go for the 64-bit operating system. You have a 64-bit CPU from what you say, so you might as well take advantage of the extra optimizations of 64-bit Ubuntu and the longer numbers and more precise mathematics of the 64-bit CPU to speed up some of the things you'll be doing with your computer.

It's not like Windows where most software is still only 32-bit; in Linux it's rare to find software that is not 64-bit, and the proprietary 32-bit software can still run without troubles on your 64-bit OS.

---

