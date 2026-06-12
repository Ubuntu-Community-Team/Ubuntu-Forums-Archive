---
title: "Boot Problems after Updates"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by tobitzki.vitto on 2010-11-22
Good morning! (from here in the Philippines)

I would like to ask how to solve this problem I just had.

First of all, as I am typing this post, I am using my *other* computer, which runs Windows XP SP2.

Yesterday, I have finished completing the updates which the Update Manager always pops out every time I turn on my **Ubuntu Lucid Lynx 10.04 LTS** (I hope I got that right) computer. Then I turned it off. 

The problem began after 5 hours, when I need to use the computer and then there is a message that appeared:

```
udevadm trigger is not permitted while udev is configured
```

then after for about a minute or two, the following appeared:

```
Gave up waiting for root device, Common problems:
- Boot args (cat /proc.cmdline)
  - Check rootdelay = (did the system wait long enough?)
  - Check root = (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/d1b2a12-ff6c-4ad8-aa33-d24714d0084f does not exist! Droppinng to shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1 Ubuntu 11) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)    
```

Things like that...

I hope you may help me immediately cause my education is on the line here..

I would also like to request a complete step-by-step procedure on how to fix this and my computer has no CD Drive.

THANKS!

---

### Post by wilee-nilee on 2010-11-22
Boot a live Ubuntu cd on that computer and run the bootscipt in my signature. Come back to the thread open a reply click on the # in the reply panel and paste all the text from the generated file that appears by running the boot script.

---

### Post by tobitzki.vitto on 2010-11-22
@ wilee-nilee ::: uhmm, the problem is i don't have an Ubuntu LiveCD and even if I do have, my computer does not have a CD-Rom Drive...

Thanks for the reply!

---

### Post by wilee-nilee on 2010-11-22
> **tobitzki.vitto said:**
> @ wilee-nilee ::: uhmm, the problem is i don't have an Ubuntu LiveCD and even if I do have, my computer does not have a CD-Rom Drive...

Thanks for the reply!

Load a thumb drive, you will get some answers but without a bunch of missing information , you may have a nice doorstop do you get what I'm saying here.

I will guess you have a wubi install is this correct? did you install Ubuntu from a Live windows environment.

This information alone is extremely important.

You want quick help but are unable to do some basic work to get it, what is up with that.;)

In your words.
> I hope you may help me immediately cause my education is on the line here..

At the least you should have a recovery thumb for all operating systems this is just logical practice.

---

### Post by weiersc on 2010-11-28
I have exactly the same problem.

I did a distro upgrade from 10.04 to 10.10 and immediately I received the same error:

Gave up waiting for root device, ALERT! /dev/disk/by-uuid/xxxxxxxx does not exist
Dropping to shell.

I can re-boot using the old 10.04 kernel, but not any of the new 10.10 kernels.

To make things more complicated: the 10.10 installation disk will not work - it also drops to the busybox shell with an error: unable to find a medium containing a life file system.

I have even tried to download the latest Natty installation disk and I get exactly the same error - except that the Busybox is now version 1.17 in stead of the 1.15.

Today I re-installed 10.04 without any difficulty. I did all the system updates and then I did the Distro update and exactly the same problem occurred on a completely clean system.

I attach the boot information that you requested above.

Thank you in advance for your wisdom.

---

