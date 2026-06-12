---
title: "Installation advice"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by Nikhil_07n on 2009-10-05
I'm going to install ubuntu but I don't have required space on the windows(XP) partition..

Can I install it on another partition?
Also, Would I be able dual boot?

---

### Post by wildman4god on 2009-10-05
sure thats what many people do, do you have another partition, if you do just start the ubuntu installer and select install to largest contiguous space and this should select your partiton, if it selects the wrong one then you'll have to do a manual partition, but let me know first if you have another partition before I get into manual.

---

### Post by Cruth on 2009-10-05
U have to install it on another partition. And yes u can have dualboot.

---

### Post by Nikhil_07n on 2009-10-05
Thanks for the quick reply(s).
Check the attachment. It IS the partition I want.

And one more question, what's the difference between 3GB and 4GB installation?

---

### Post by Zimmer on 2009-10-05
I think you need to do a bit more research before you attempt an install and to examine your motives for doing so.
see
 [http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu-2/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu-2/)

How big is your hard drive? do you have more than one?
see 
[http://members.iinet.net.au/~herman546/p17.html](http://members.iinet.net.au/~herman546/p17.html)

particullarly the part titled 
'Preparing to install'.

Have you tried the Live CD ?

---

### Post by tpjk on 2009-10-05
yes, you can install ubuntu to a different partition.
and yes, you will be able to dual boot.

if you have any specific questions as to how to set everything up you can PM me.

---

### Post by wildman4god on 2009-10-05
first you need to boot from the cd not launch it from inside windows. Reboot your computer, watch the post screen it should say what key to press to get into your bios, once in the bios set your system to boot from cd first then press F10 to save and exit the bios the system should then boot into ubuntu live cd (after selecting your language and selecting try ubuntu) from there you can try out the ubuntu environment though proformace will be reduced, but once your done playing around select the installer icon on the desktop to get stuff going, from there you will fill out information such as time zone, etc... and then you'll eventually get to the partition editor. there you will either select dual boot option, if you only have one partition with XP on it, if you have 2 or more partitions then you'll have to do a manual partition to select the one you want to install ubuntu on.

---

### Post by Nikhil_07n on 2009-10-05
Yes. I have tried it.

The partition on which I'm installing is 15GB with 5GB free.

> Set up a dual-boot. If you don&#8217;t want to wait on getting compatible hardware or if you aleady have compatible hardware, go ahead and set up a dual-boot with Windows. That way, you&#8217;ll be able to customize Ubuntu (the live CD settings don&#8217;t get saved) and run it at native speeds (the live CD runs more slowly than a full installation), but you&#8217;ll also have access to Windows if you need to run back to the safety of familiarity. The Ubuntu installer is fairly user-friendly, but if you&#8217;re still scared of messing around with partitions and boot loaders, there&#8217;s a project called Wubi that allows you to install Ubuntu from within Windows. It sets up Ubuntu as a removable application in Windows and uses Windows&#8217; boot loader to pick which operating system to boot into.

Advice for Me.:lolflag:

---

### Post by 3rdalbum on 2009-10-05
> **Nikhil_07n said:**
> Yes. I have tried it.

The partition on which I'm installing is 15GB with 5GB free.

Well, it's actually not.

Ubuntu installs onto its own format of partition, not to fat32 or NTFS (the Windows filesystems). So in order to install onto that 15 gig partition, the Ubuntu installer either needs to erase the whole partition and format it to ext3/ext4, or resize the partition downwards and create a new partition for itself in the newly-created space.

5 gigabytes is a bare-minimum kind of install. As in, currently my operating system and programs alone take up more than that. 5 gigs will see you installing very few programs and creating very few files. Partitioning also causes a slight loss of space, too, and your existing 10 gigs of data is probably scattered all over the existing partition. The Ubuntu installer will move the files that are inside the last 5 gigs of space on the partition, but it doesn't do a perfect job and this will cause a loss of contiguous space.

In short, your 5 gig frugal install is looking more like 4.5 gigs. Oh, and then you've got some swap space... which could probably eat up another 512 megs.

Why not just grab another internal hard disk, you can get them very cheaply these days, and dedicate it to Ubuntu. Even 160 gigs is good.

---

### Post by praveesh on 2009-10-05
I would recommend you to install Ubuntu in the first partition . Because that will increase the total performance of the Ubuntu .

---

### Post by praveesh on 2009-10-05
If you can't install in the first partition, try to install in the next partition.  Because, if you install in the final partitions, the speed/performance/responsivity of the Ubuntu will be reduced and you will soon come to this forum complaining that Ubuntu is slower than windows xp.

---

