---
title: "Partition Sizes? Help"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by davequig on 2011-05-18
Hi I have windows 7 starter installed. I want to install Ubuntu 10 as a dual boot. I have 116Gb of free space.
Should each partition be "primary" or "logical"?
How much space should each partition have?
How many partitions(mount points) should I include?
mount points:
/
/boot
/home
/tmp
/usr
/var
/srv
/opt
/usr/local

---

### Post by mcduck on 2011-05-18
unless you have a specific reason to, you shouldn't make too many separate partitions. That would only result in having too much space on one partition while running out on space on other, unless you are able to reliably predict how much space you are going to use on each one.

So, I'd recommend simply creating a root partition, as large as you can, and then the required swap partition (as large as the amount of RAM on your computer if you wish to be able to suspend the machine).

If you want, add a separate /home partition or storage partition to keep your personal stuff safe if you need to reinstall Ubuntu at some point. In this case your root partiton doesn't need to be that large, as it's your personal files that will be taking most of the space.

Ubuntu doesn't care if it's partitions are primary or logical ones. So the only rule here is the basic partitioning rule of max 4 primary partitions, or three primary ones plus one extended partition (containing as many logical ones as you wish).

So, the two options I'd recommend (assuming you have 4GB of RAM)
112GB /
4GB swap

or:

20GB /
92GB /home (or storage partition mounted where ever you want to)
4GB swap

---

### Post by davequig on 2011-05-18
i have heard that the space for swap should be double your RAM?

---

### Post by mcduck on 2011-05-18
> **davequig said:**
> i have heard that the space for swap should be double your RAM?

That was true a long time ago, when the amounts of RAM in computers were much smaller.

These days it's quite unlikely your system would ever actually need to start swapping, so the rule isn't valid any more.

Nowadays the rule is that you need equal amount of swap as you have RAM if you wish to suspend the computer. (since data from RAM is written to swap when suspending). If you don't use suspend, then you probably will never actually use swap at all, but considering the large amounts of disc space people have it makes sense to have at least a small swap partition just in case.

---

### Post by ajgreeny on 2011-05-18
I fully agree with mcduck, and would say keep it to the three partitions, /, home and swap.

If you don't have a separate home you will probably kick yourself next time you need to install Ubuntu, as it does make that job so very much easier.

See [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome") for more details.

---

### Post by davequig on 2011-05-18
is it unnecessary to create a /boot partition?
my ram is only 1gb as its a crappy little netbook so should i double swap in this case.

thanks for all the feedback btw

---

### Post by ajgreeny on 2011-05-18
> **davequig said:**
> is it unnecessary to create a /boot partition?
my ram is only 1gb as its a crappy little netbook so should i double swap in this case.

thanks for all the feedback btw
Quite un-necessary to have a separate /boot these days; to be honest, I'm not quite sure why it was ever a very good idea, but maybe there were good reasons in the past.

I would suggest 2Gb swap in your hardware situation.

---

### Post by mcduck on 2011-05-18
> **ajgreeny said:**
> Quite un-necessary to have a separate /boot these days; to be honest, I'm not quite sure why it was ever a very good idea, but maybe there were good reasons in the past.

I would suggest 2Gb swap in your hardware situation.

Separate /boot is only useful in rather special cases, for example if you have a large root partition and very old motherboard that can't boot from that large drives. Or if you use some form of encryption for your root partition.

For most users separate /boot will just result in problems (running out of space on boot), or wasted space (/boot being larger than you need).

What comes to swap with 1GB of RAM, I'd go for 1GB of swap. Most likely even that's much more than what will be used (apart from suspending, of course). And for the reference, my laptop has 1GB of RAM, I'm still waiting for the day when it actually needs any swap. :D

---

### Post by Wim Sturkenboom on 2011-05-18
Separate boot partition is a nuisance for home use. Each kernel update will go in there and if you don't check and clean out regularly, you'll one day have a system where a kernel update failed.

For home use /, /home and swap will do. A standard install is probably still under 5GB. Leave space for additional software, updates etc and I think that 20GB for a root partition should be plenty (mine is 25GB and I have about 5 in use with Ubuntu 10.04). 1GB swap and the rest for /home

With a crappy netbook, I would consider other distros. Possibly lubuntu or xubuntu might be better choices as your processor power is a bit limited. This is posted from a netbook with 512MB and running crunchbang.

---

### Post by davequig on 2011-05-20
I have installed ubuntu as you guys recommended. My netbook however automatically loads windows. What have I done wrong?

---

### Post by ubume2 on 2011-05-20
> **davequig said:**
> I have installed ubuntu as you guys recommended. My netbook however automatically loads windows. What have I done wrong?

You apparently installed Ubuntu with a flash drive. And a grub menu should have been created when you installed Ubuntu. If you could borrow an external CD drive, create a LIVECD. First you need to check your hard disk to see if Linux and swap file are present using gparted. If they are present, then you need to try to restore or create a grub menu.

For that see:

[http://blog.ecafechat.com/2010/04/13/recover-grub-after-windows-installation/](http://blog.ecafechat.com/2010/04/13/recover-grub-after-windows-installation/)

or,

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by davequig on 2011-05-20
yeah someone told me it wud be the grub.....I have zero chance of getting my hands on an external cd drive, what is gparted and how do i see if linux files are present. Yes i installed off a usb.

thanks. patience is a virtue.

---

### Post by ubume2 on 2011-05-20
If you have a netbook and installed a regular Ubuntu 10.XX install, I'm not sure how well that would work. I have not used a netbook.  You might look at this:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

Can you boot from the USB device, and is it a live usb?
Can you go to System Settings and use gparted to view your partitions?
Or as an alternative, go to the terminal and report the output of 
```
$sudo fdisk -lu >>fdisk.txt
```

If all the suggestions made do not result in a fix try reposting with a subject something like Ubuntu 10 grub missing on Netbook.  Apparently you solved the partition problem. Right? (Note: Usually just set up swap and a / partition)

---

