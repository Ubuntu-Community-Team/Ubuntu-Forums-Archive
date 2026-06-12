---
title: "Not enough disk space to install updates?"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by zZhou on 2009-07-04
I just recently installed Ubuntu on my laptop. After installation and setup, Update Manager popped up and prompted me to install updates. I tried to install the new updates, but an error message appeared saying that I only had 272 mb of disc space left. 

When I go back to windows, it says I have over 252 gb of space. So why is all the disk space going to Vista? Is there a way to repartition the disk so I can install the ubuntu updates?

Thank you.

---

### Post by diablo75 on 2009-07-04
Did you install using Wubi?  Because if you did, I think there was an option during the install that asked you how much space you would like to allocate towards Ubuntu.

As for "repartitioning" (in this case) I'm not sure if it can be done because you still only have one NTFS partition on your PC and the "partition" that Ubuntu is using is actually just a folder that Ubuntu is tricked into thinking is a real ext filesystem... There's probably a way to go about doing this but someone else will have to help with that.  If it were me, I'd backup anything important from Ubuntu, then re-install from a Live CD (booting off of it) to do a REAL repartitioning of the hard drive where a real ext partition will be created for installation.

Now if you did use a Live CD and we're talking about an NTFS partition next to other ext3/4 partitions, you can use a [gParted Live CD]("http://gparted.sourceforge.net/") to resize your partitions.

---

### Post by QIII on 2009-07-04
Did you install in a dual-boot configuration or did you use Wubi to install inside windows?

Could you post the results of 

sudo fdisk -l   

(That's a small "ell" not a one.)

---

### Post by zZhou on 2009-07-04
Um.... Complete beginner question: How do you access the CLI?

I installed Ubuntu by downloading the disk iso, not with Wubi. I installed with the first option. I forgot exactly what its called, but it allowed me to dual boot Ubuntu and Vista.

Diablo75: Sorry, but I can not understand in the last 2 paragraphs in your post.

---

### Post by QIII on 2009-07-04
I'll avoid the keyboard shortcuts for now.

Applications | Accessories | Terminal

---

### Post by philcamlin on 2009-07-04
boot into your live cd and change the size of your hard disk space

---

### Post by diablo75 on 2009-07-04
> **zZhou said:**
> Um.... Complete beginner question: How do you access the CLI?

I installed Ubuntu by downloading the disk iso, not with Wubi. I installed with the first option. I forgot exactly what its called, but it allowed me to dual boot Ubuntu and Vista.

Diablo75: Sorry, but I can not understand in the last 2 paragraphs in your post.

To access the command line (which is like the "Command Prompt" CMD in Windows/DOS) click Applications>Accessories>Terminal.  Then you can type/paste in whatever you need/want.

I think the first option on the installer is "Guided Resize", and then you have to specify how large you want the new Ubuntu partition to be.

Anyway, ignore the last part of my previous post except for the part about gParted.

It is a bootable CD you can use to resize your partitions and it is very easy/simple.  Just download the ISO and burn it to a disc like you did with the Ubuntu Live CD.  Boot from it.  Once it's up, you'll just right-click on the larger NTFS partition you have Vista installed on, and select resize.  The type in a smaller size by number or visually grab the edge of the partition and drag it down so it's smaller.  Then do the opposite with the ext3 partition you have Ubuntu installed on; dragging it out to fill in the space you made by shrinking the NTFS side.  Then click the apply button at the top and take a nap (it can sometimes take a while to do a resize).

---

### Post by zZhou on 2009-07-04
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a127dc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37162   298502741    7  HPFS/NTFS
/dev/sda2           37488       38913    11451392    7  HPFS/NTFS
/dev/sda3           37163       37487     2610562+   5  Extended
/dev/sda5           37163       37465     2433816   83  Linux
/dev/sda6           37466       37487      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order.

Is this it?


Ok I will try the other options to resize.

---

### Post by QIII on 2009-07-04
Just a hint before you resize (and something you should have done before installing Ubuntu):

Run defrag a couple of times in Windows.

---

### Post by QIII on 2009-07-05
Yeah.  Your Linux partition is a tad bit small...

---

### Post by diablo75 on 2009-07-05
> **zZhou said:**
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a127dc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37162   298502741    7  HPFS/NTFS
/dev/sda2           37488       38913    11451392    7  HPFS/NTFS
/dev/sda3           37163       37487     2610562+   5  Extended
/dev/sda5           37163       37465     2433816   83  Linux
/dev/sda6           37466       37487      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order.

Is this it?


Yup, that's it.  So your drive is laid out something like this:

[NTFS w/Vista (almost 300MB)][Hidden windows recovery partition]{[Linux root partition][Linux swap]}

I've denoted the {extended} "container" partition with these {squiggly brackets}.

So what you'll need to do is shrink the first NTFS (the largest) partition which houses Windows, followed by MOVING the second NTFS partition over to but up against the first one.  Then you can expand/stretch the extended partition out to fill the gap, and then expand the Linux partition that lies *within* the extended partition out to fill the gap.

---

### Post by zZhou on 2009-07-05
Thanks for all the help. I think that I have successfully increased the size of the Ubuntu portion to ~100 gb. 


Thanks again

---

