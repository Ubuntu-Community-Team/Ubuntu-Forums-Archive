---
title: "Is there a way to install ubuntu using only ONE primary partition"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by tanha on 2010-06-03
Or do you have to have at least two for / and swap? Would LVM on the alt CD solve install to only one partition (I have three primary partitions already in use), for example?

---

### Post by nhasian on 2010-06-03
you dont HAVE to have a swap file if you have a lot of memory but its required if you want to be able to hibernate a laptop. also you can put the swap partition in an extended volume.  it doesnt have to be a primary partition.

---

### Post by tanha on 2010-06-03
> **nhasian said:**
> you dont HAVE to have a swap file if you have a lot of memory but its required if you want to be able to hibernate a laptop. also you can put the swap partition in an extended volume.  it doesnt have to be a primary partition.

So, I can make an extended for swap and still have room for a primary partition for /?

---

### Post by howefield on 2010-06-03
> **nhasian said:**
> you dont HAVE to have a swap file if you have a lot of memory but its required if you want to be able to hibernate a laptop. also you can put the swap partition in an extended volume.  it doesnt have to be a primary partition.

In this example the whole Ubuntu install would need to be put in an extended partition, not just the swap. The extended partition would count as the fourth "primary".

---

### Post by tanha on 2010-06-03
> **howefield said:**
> In this example the whole Ubuntu install would need to be put in an extended partition, not just the swap. The extended partition would count as the fourth "primary".

OK... But, I thought that / had to be on a primary partition, no?

---

### Post by howefield on 2010-06-03
> **tanha said:**
> OK... But, I thought that / had to be on a primary partition, no?

No, Ubuntu can be installed on either a primary or extended (logical) partition.

---

### Post by tanha on 2010-06-03
> **howefield said:**
> No, Ubuntu can be installed on either a primary or extended (logical) partition.

Ubuntu can be installed entirely in an extended? Didn't know that. But, Thanks!

---

### Post by howefield on 2010-06-03
> **tanha said:**
> Ubuntu can be installed entirely in an extended?

Yep, as you know you can have only 4 primary partitions, one or more of those partitions can be an extended partition containing as many logical partitions as you need.

In your example, you have 3 primary partitions, and making the fourth one an extended volume means you can partition that into 3 logical partitions, eg, / /home and swap.

You are not restricted to 3 logical in your extended partition, I'm just using that to illustrate. Can't remember the limit to be honest.

Actually, there are workarounds to the 4 primary limit, but I believe they may be a bit flaky.

---

### Post by tanha on 2010-06-03
> **howefield said:**
> Yep, as you know you can have only 4 primary partitions, one or more of those partitions can be an extended partition containing as many logical partitions as you need.

In your example, you have 3 primary partitions, and making the fourth one an extended volume means you can partition that into 3 logical partitions, eg, / /home and swap.

You are not restricted to 3 logical in your extended partition, I'm just using that to illustrate. Can't remember the limit to be honest.

Actually, there are workarounds to the 4 primary limit, but I believe they may be a bit flaky.

Well, it worked. Thanks again to you both!

---

### Post by srs5694 on 2010-06-03
Others have given good advice. I just want to elaborate on a couple of points for educational purposes....

> **howefield said:**
> You are not restricted to 3 logical in your extended partition, I'm just using that to illustrate. Can't remember the limit to be honest.

The theoretical limit is one less than half the number of sectors on the disk, at least based on the data structures involved. For a 2 TiB disk (the biggest that can be handled by the MBR partition scheme), that works out to over 2 billion partitions. (These would all be 512-byte partitions, though, and what you'd need with 2 billion 512-byte partitions I don't know.) If there's a limit in the Linux kernel, I don't happen to know what it is, but I've successfully put more than sixteen logical partitions on a disk (plus three primaries) as a test and it was fine.

> Actually, there are workarounds to the 4 primary limit, but I believe they may be a bit flaky.

The only workaround I know of that's within the MBR scheme is to have a boot loader or some other utility store multiple MBR tables and swap them in or out on a case-by-case basis. This will permit each OS to have its own selection of primary partitions, but no OS will be able to access all of them simultaneously. I've heard of boot loaders that enable this, but I don't recall the details. I shudder to think of the problems that could ensue from careless use of this sort of system.

A longer-term and much less flaky solution, which we'll all be using in a few years, is the GUID Partition Table (GPT) system, which is a replacement for the aging MBR system. GPT supports 128 partitions by default (that value can be changed), with no primary/extended/logical distinction. [Linux is well-prepared for GPT,](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) so you can use GPT with Linux today if you like. The problem is that Windows is not so well-prepared. Although Windows Vista and 7, as well as some earlier versions depending on platform, support GPT data disks, Windows only supports booting from GPT disks on systems that use an Extensible Firmware Interface (EFI) rather than the more common BIOS firmware.

There is a flaky hybrid between GPT and MBR, known as a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which enables a disk to use GPT for all its partitions but to put up to three of them in the MBR to function as MBR primary partitions. This can keep Windows happy if you need to dual-boot Windows with an OS that uses GPT. Apple relies heavily on hybrid MBRs for its Boot Camp system for dual-booting OS X with Windows on Apple hardware. It's also possible to use a hybrid MBR to dual-boot Windows and Linux; however, hybrid MBRs are flaky and dangerous, and they've got few advantages over a regular MBR with Linux in logical partitions, so I don't recommend doing this except in extraordinary circumstances. (The only practical advantage I can think of is that the GPT-only partitions can be interspersed with the hybridized MBR partitions more flexibly than you can intersperse primary and logical partitions.)

---

### Post by Kellemora on 2010-06-03
Good information to know SRS!!!!!

I don't know about Windows Vista or 7, but XP we put on Partition one.
Then put all the other stuff on extended partitions.

Just fooling around for the heck of it, we installed XP-Pro on one XP-Home on a 2nd primary, then on extendeds, Win98, Win95 and even Win3.11, plus CentOS, Debian, Ubuntu.
If anything at all good came out of it, I was able to pull a bunch of old software I liked and had forgotten about to play with.
The only hard part was getting XP-Home to load, Windows likes to be the BOSS, hi hi.........  Everything else was a snap!

TTUL
Gary

---

### Post by anewguy on 2010-06-04
Something that may be worth mentioning for others reading this post and also wondering about needing a separate partition for swap.  Swap doesn't have to be in a partition - it can be in the file system (like the page file in Windows).  For anyone interested in doing so, search the forum, then post a thread if you have questions.

Dave ;)

---

### Post by varunendra on 2010-06-04
> **anewguy said:**
> Something that may be worth mentioning for others reading this post and also wondering about needing a separate partition for swap.  Swap doesn't have to be in a partition - it can be in the file system (like the page file in Windows).  For anyone interested in doing so, search the forum, then post a thread if you have questions.

Dave ;)

Method [here]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/").
Method with Example [here]("https://help.ubuntu.com/community/SwapFaq"). (See 'example of making a swap file' on the linked page.)

---

### Post by Herman on 2010-06-04
> Something that may be worth mentioning for others reading this post and  also wondering about needing a separate partition for swap.  Swap  doesn't have to be in a partition - it can be in the file system (like  the page file in Windows).  For anyone interested in doing so, search  the forum, then post a thread if you have questions.:)
I agree, I like to use the following how-to and create a swap file instead of a swap area, [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile")  - by iva2k.

Thanks varunendra for your links, I'll check those ones out too.

---

