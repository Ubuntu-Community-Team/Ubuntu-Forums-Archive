---
title: "Slightly Different XP/Vista thread"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by spookyct on 2009-03-20
I just bought a new machine pre loaded with Vista, and unfortunately I'm required to use XP for work(only thing that works with our VPN software).  I plan on using Ubuntu for everything else.  Also, id like to keep Vista on here since I just paid for it :(.

My question is what is the method for installing?  I suspect that I should resize Vista, install XP, then install Ubuntu last???

Has anyone done this before?  Anything to watch out for?

Also, what's the deal with this factory image?  I guess that's how I install Vista again?  Are there any special considerations there?  Finally, this is a 64 bit system; is 64bit Ubuntu stable? better?

Thanks!

---

### Post by SunnyRabbiera on 2009-03-20
A triple boot is possible, though it will limit some stuff like space and partitioning.
Be careful, and always install windows first.

---

### Post by egalvan on 2009-03-20
If this is a desk-top, see if you can install another hard drive to ease the triple-boot install.

If no extra disks are possible, then you will have to plan very carefully. A single drive will limit your options.

---

### Post by SunnyRabbiera on 2009-03-20
Indeed, its advised to compress the filesystem and defrag in Vista before adding anything in.

---

### Post by kpatz on 2009-03-20
Depending on how much RAM you have, you could install Virtualbox on Vista and then run XP and Ubuntu in virtual machines... just another option to triple-booting.

---

### Post by spookyct on 2009-03-20
> **kpatz said:**
> Depending on how much RAM you have, you could install Virtualbox on Vista and then run XP and Ubuntu in virtual machines... just another option to triple-booting.

Interesting...  Ubuntu running on top of Windows scares me a little though.

---

### Post by spookyct on 2009-03-20
> **kpatz said:**
> depending on how much ram you have, you could install virtualbox on vista and then run xp and ubuntu in virtual machines... Just another option to triple-booting.

6gb

---

### Post by sandyd on 2009-03-20
> **spookyct said:**
> 6gb
thats wayyyyyyyyy more than enough to run a virtual machine

im pretty sure you have enough to run one. Its uaually the RAM that limits the VIrtual machine speed. 

use someting like virtualbox-ose or qemu

---

### Post by Joeb454 on 2009-03-20
It may be best to run XP in a virtual machine in this case. For Windows to play nice, it's easier to install in this order (I had to do it this way once)

XP &#8594; Vista &#8594; Ubuntu

That way, Vista detects the XP install and adds it to the boot loader for Vista, and Ubuntu will detect Vista's bootloader :)

---

### Post by easybake on 2009-03-20
> **spookyct said:**
> ... what's the deal with this factory image?  I guess that's how I install Vista again?  Are there any special considerations there? 
The factory image, from what I know (which isn't too much) is basically a recovery cd. They can range from a full install or just an addition which relies on a "ghost" or hidden partition that is used to recover the system. A consideration would be that if you install ubuntu and completely reformat your hard drive you may not be able to re-install vista. You should be fine if you are careful.

>  Finally, this is a 64 bit system; is 64bit Ubuntu stable? better?
I've always had better luck with 32 bit systems just because not all programs give 64 bit options. Which can be frustrating. As for stability I think either way you should be fine.

> My question is what is the method for installing?  I suspect that I should resize Vista, install XP, then install Ubuntu last???

Has anyone done this before?  Anything to watch out for?

There are a couple different ways to do it. It all really depends on what boot loader you want to use. 

*If you want to keep the vista bootloader to manage your triple boot you are going to have to use a program like [easyBCD]("http://neosmart.net/dl.php?id=1") and follow different steps.*



**I would suggest** to use the alternative with grub being the main boot loader. You have the basic idea but you just need to add a few extra steps.

First you can resize your partitions with Gparted. You can find this on the Ubuntu live cd. Shrink the Vista partition down, create an NTFS partition for XP, an ext3 partition for Ubuntu, and another parition to be used as swap space around (1.5 gigs)

Once you have created the three paritions. Right click on the vista partition in Gparted. Click Manage Flags. Remove the "boot" check mark and add a check mark to "boot" for the xp NTFS parition.

apply changes and quit. 

**Install XP**.

When finished put back in the Ubuntu disc. Before installing Ubuntu go back into gparted and remove the "hidden" flag you added to the vista partition. 

**Install Ubuntu.** When it asks for mountpoints use the ext3 parition you created as your root or "/" parition. and the 1.5 gig partition as a "swap". Reboot and notice your new boot menu.

If you encounter that you can't boot into vista, it is easily fixed.

---

### Post by easybake on 2009-03-20
> **Joeb454 said:**
> It may be best to run XP in a virtual machine in this case. For Windows to play nice, it's easier to install in this order (I had to do it this way once)

XP &#8594; Vista &#8594; Ubuntu

That way, Vista detects the XP install and adds it to the boot loader for Vista, and Ubuntu will detect Vista's bootloader :)


This way also works but you end up with 2 different boot screens. If you hide the XP partition before installing Vista. Vista won't pick up xp and create a second boot screen.

---

### Post by lisati on 2009-03-21
> **easybake said:**
> The factory image, from what I know (which isn't too much) is basically a recovery cd. They can range from a full install or just an addition which relies on a "ghost" or hidden partition that is used to recover the system. A consideration would be that if you install ubuntu and completely reformat your hard drive you may not be able to re-install vista. You should be fine if you are careful.


The copy of Vista that came with my newer laptop has a tool to create a set of two recovery DVDs from the recovery partition (or one if I use a double layer disk). One of the first things I did was use it just in case I clobbered the recovery partition and needed Vista back again for some reason.

---

### Post by Al Fischer on 2009-03-21
I bought a new Lenovo (IBM) T61 last year and the FIRST thing I did (before XP that it came with was even booted) was creade a B/U image using Acronis True Image. THEN after the install I made the 'Restore Disks'. Not for if I clobber the OS but for WHEN I clobber it!

I have been trying multi boot usine GRUB4DOS by building my OS on a separate HD and then copying the image over using GPARTED. It works quie well. I am not comfortable actually doing a 2nd install of an OS and letting it resize my HD and then install. So far I have been able to build several diffenet versions of my multi boot disk HD from ONE copy of Linux, one copy of XP and one copy of DOS. I have heard that the Acronis software does not do Vista well, but I WILL NOT deal with Vista for many reasons.

You might use a second drive and try copying the entire Vista partition to it with a GPARTED live CD and see how it goes. I am not familiar with the boot sector need for Vista but GRUB4DOS is quite flexible. Also after creating your Restore Disk from your factory load you can put it on another drive to play and create another set of restore disks from that load. Most manufacturers proceedure limite creating ONE set of restore disks (and then you call them and either beg or PAY for them to send you a new restore disk) Lenove wants about $40 + shipping. UGH!

---

### Post by arapa on 2009-03-21
> Finally, this is a 64 bit system; is 64bit Ubuntu stable? better? 

I would suggest the 64-bit Ubuntu so you can use your 6 GB of RAM. 32-bit OS's are unable to use anything over 4 GB (or less). I am running it and have had no problems with stability.

---

### Post by egalvan on 2009-03-21
> **arapa said:**
> I would suggest the 64-bit Ubuntu so you can use your 6 GB of RAM. **32-bit OS's are unable to use anything over 4 GB (or less). **I am running it and have had no problems with stability.

Not quite true...

With PAE enabled, 32-bit OS can use more RAM.

The 32-bit Server kernel has that enabled.

Install the 32-bit Server edition,  then add the Desktop Environment you desire,

Or install the 32-bit Desktop version, then install the Server kernel.

Either way will get you support for 64GB RAM.


Or just go for 64bit Ubuntu... :)

---

