---
title: "finding hard disk on laptop using live cd"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by smile_sunshine on 2011-07-26
Hi there, 
I'm trying to fix an old laptop for a community group I'm involved with and install ubuntu for them. The laptop is currently saying operating system not found, but it runs the ubuntu live cd OK.

It won't install though as it says there's not 4GB of space on a hard disk - it looks to me like it can't find one at all. 

I think its quite possible the hard-disk is just broken, but I'm unsure and want to check I'm doing this right before I go back to them and say the laptop won't work. 

What do I need to type in a terminal to search for any hard-disks the laptop has and view their size etc? 

Thanks :)

---

### Post by bodhi.zazen on 2011-07-26
> **smile_sunshine said:**
> Hi there, 
I'm trying to fix an old laptop for a community group I'm involved with and install ubuntu for them. The laptop is currently saying operating system not found, but it runs the ubuntu live cd OK.

It won't install though as it says there's not 4GB of space on a hard disk - it looks to me like it can't find one at all. 

I think its quite possible the hard-disk is just broken, but I'm unsure and want to check I'm doing this right before I go back to them and say the laptop won't work. 

What do I need to type in a terminal to search for any hard-disks the laptop has and view their size etc? 

Thanks :)

```
sudo fdisk -l
```

or

```
sudo blkid
```

You can also use parted (command line) or gparted (graphical tool)

---

### Post by smile_sunshine on 2011-07-26
thanks :) 
I get nothing at all for sudo fdisk -l 
and for sudo blkid i get: 
> /dev/loop0: TYPE="squashfs" 

I'm guessing this means no working hard disk then? 

Thanks so much for your help :)

---

### Post by skatinjj on 2011-07-26
You can check in BIOS to see if the hard drive is detected.  If not, the hard drive could be defective.

---

### Post by bodhi.zazen on 2011-07-26
> **skatinjj said:**
> You can check in BIOS to see if the hard drive is detected.  If not, the hard drive could be defective.

Assuming it is a "old" laptop, the hard drive is probably kaput.

It is possible you have an esoteric piece of hardware and need to compile a custom kernel. Google search linux or ubuntu + the exact laptop and you may find additional information if this is the case.

---

