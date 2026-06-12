---
title: "how formating a partition within ubuntu"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by jdrodrig on 2009-08-13
Hi, Noob question.

I was trying to make room for a linux-swap partition for an OpenSolaris installation. 

The live Gparted CD was of no use, because I cannot make anything out of the screen. I have the box connected to a HDTV and all the resolutions offered by Gparted either dont show anything or show unreadable icons...

So I managed (I think I did) to shrink my Vista partition using the Ubuntu Live CD advanced installation, I created the partition and forced a shutdown not to continue with the installation. But it now appears, free space, unformatted.

Can I format it to linux-swap within ubuntu?

The solaris installation shows it as free, but it does not let me format it, at least through the GUI of the LiveCD.

---

### Post by starcraft.man on 2009-08-13
Before answering your question, I'd like to point out that on a single machine with multiple *nix installs you really need only one linux swap file. If you already have one for Ubuntu (as you should) then this process is entirely unnecessary.

As for formatting and partitioning in Ubuntu just install gparted from the repositories by your preferred means and start it up by System > Admin > partition editor. The package required is called **gparted**. If you need help installing see my sig. Note, that any partition to be edited must be unmounted and not in use.

---

### Post by LewRockwell on 2009-08-13
you've read up on ONLY using Vista utilities to work with Vista partitions!?!

.

---

### Post by jdrodrig on 2009-08-13
Thanks for the reply. I tried gparted within ubuntu, but I am now running against the max 4 primary partitions limit (that until today, I was totally unaware of)....any suggestions how to add a partition for solaris?

Btw, being a primary partition is not a requirement to be bootable, right?

I have so far
/dev/sda1 fat16 70mb dell utility
/dev/sda2 ntfs 15Gb recovery
/dev/sda3 ntfs 344Gb Vista64
unallocated 47.50 Gb
/dev/sda4 extended
   /dev/sda5 ext3 
   /dev/sda6 linux-swap

And I want those unallocated 47.50Gb to be for opensolaris...opensolaris documentation suggests formating it linux-swap and during the installation marked it to be taken over by solaris...

---

### Post by starcraft.man on 2009-08-14
No linux or unix OS has a requirement to be primary, including solaris if you so want to try it. 

As to the partition, I'd move all of the free space into the extended partition. Once it's there, ya can make as many more partitions as ya feel like. I'm unfamiliar with installing opensolaris, did do it once but that was while ago. I don't really understand why ya would need to make a 50 GB partition swap space just to have solaris take it over later and convert it to what I assume will become zfs. If it says so however, I guess do it. I think that answers your questions, do ya really think you'll need 50GB for a root? That's a bit excessive, unless solaris has become massively bloated...

---

### Post by jdrodrig on 2009-08-14
Thanks starcraft....

Well, I am installing opensolaris because it is the only free OS on which their sunstudio development kit is supported; so I want some space for my coding projects. I think the recommended solaris installation is 13gb....

So, to implement your suggestion, would the ubuntu live cd installation process let me do this rearranging of partitions; I am asking because my problem started not being able to use gparted live cd due to screen problems.

Thanks again.

---

