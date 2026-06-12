---
title: "tweaks in ubuntu dor ssd's?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by jarongg on 2010-02-19
just installed a ssd into my netbook. are there any tweaks for ubuntu (jaunty) that i can do to make the most of my ssd?

---

### Post by NightwishFan on 2010-02-20
I only know of two performance related tweaks. You can mount your SSD with noatime (which is something about updating file access times). I have heard that it will improve performance, but I actually do not know what it does so I will not advise it. You could search more on the matter or ask for help here of course.

The tweak I know and understand is to use the No-Op I/O scheduler. By default Ubuntu uses a scheduler called CFQ (Completely Fair Queueing), which has optimizations to make up for hard disk physical seek time. NOOP does not have such optimizations, which makes it suited for a disk that has no physical movements like an SSD. You can boot Ubuntu to use the NOOP scheduler temporarily to test for any noticeable performance improvements. After a reboot, it will revert to the default CFQ scheduler.

If you are using Karmic, this will make using the NOOP scheduler. There is a way to set a scheduler for a specific device, I am unsure how to make the change permanent. (This is not as complicated as it sounds):
[LIST=1]
[*]While booting, hold in the shift key until a menu appears that lists Ubuntu kernels.
[*]The first option in the list should be the latest Ubuntu kernel. When you have it highlighted, press "E" to edit it.
[*]Tap the down key until you are on the line titled "Kernel" and push the "END" key.
[*]Your cursor will be at the end of the line. Type: elevator=noop
[*]Press CTRL+X to boot.
[/LIST]

I can help you make the change permanent if you want.

About NOOP:
[http://en.wikipedia.org/wiki/Noop_scheduler](http://en.wikipedia.org/wiki/Noop_scheduler)

---

### Post by jarongg on 2010-02-20
is the noop scheduler better than deadline? i have it set to deadline right now.

bump for more suggestions.

---

### Post by NightwishFan on 2010-02-20
The schedulers are not "better" than one another except in some cases. CFQ is the default because it seems to have the best average performance. Deadline has been shown to do better on high performance disks or databases. NOOP is simple, and uses less CPU, but does not optimize for any sort of situation. The last one is Anticipatory, which is suited for hard disks, but it is largely replaced by CFQ.

NOOP is said to be best on media with no phyiscal movements, such as flash or SSD drives. Optimising I/O for physical movement would be a waste on such disks. Unless you really know otherwise, CFQ is the best option.

---

### Post by jarongg on 2010-02-21
well i thought i had deadline made permanent, but i don't see it in the menu.lst file. can you tell me how to make the noop scheduler permanent? i would appreciate it.

---

### Post by NightwishFan on 2010-02-21
Ah, you are using Jaunty. That simplifies things.

[LIST=1]
[*]Press Alt+F2 and type: gksudo gedit /boot/grub/menu.lst
[*]Find the kernel you are using, and look for the line that ends in quiet splash.
[*]Append this at the end of the line: elevator=noop
[*]Save the file and reboot.
[/LIST]

To check if it works after a reboot, type this command. The one in brackets is the current IO scheduler. Replace "sda" for your main drive.
```
cat /sys/block/sda/queue/scheduler
```

For example mine comes back with:
```
virgil@linux-g1yx:~> cat /sys/block/sda/queue/scheduler 
noop anticipatory deadline [cfq]
```

---

### Post by jarongg on 2010-02-21
that worked perfectly! thanks.

---

### Post by jarongg on 2010-02-24
buump!

---

### Post by NightwishFan on 2010-02-24
I hear the new kernel 2.6.33 may have specific new features for ssd's. You will have to  wait until Ubuntu adopts it or perhaps use something like Debian Unstable.

I do not think 2.6.33 is out yet, it is still in release candidate.

[http://kernelnewbies.org/Linux_2_6_33](http://kernelnewbies.org/Linux_2_6_33)

---

### Post by 3rdalbum on 2010-02-24
> **jarongg said:**
> just installed a ssd into my netbook. are there any tweaks for ubuntu (jaunty) that i can do to make the most of my ssd?

What sort of SSD?

If it's a 2.5 inch SSD and it was relatively expensive, then you're probably pretty much good to go. Try the noop scheduler, use noatime when mounting your SSD, and ignore the people who tell you to use ext2 because it doesn't make a lot of difference.

If it's smaller than 2.5 inches and really cheap, then put your HDD back in. Cheap SSDs are horrible.

---

### Post by NightwishFan on 2010-02-24
Is relatime much worse than notime? Or is that only relevant on SSDs and not disks?

---

### Post by alex_o on 2010-08-11
how to make this work even after kernel updates(update-grub)

sudo gedit /etc/default/grub

find the line which says:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and replace it with:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=noop"
```
or
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=deadline"
```

---

