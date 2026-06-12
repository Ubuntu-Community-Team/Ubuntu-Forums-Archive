---
title: "Ubuntu alongside Vista help needed"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by 2step786 on 2011-05-02
After trying out Ubuntu from a live CD, I've been impressed with the support of Ubuntu as well as its minmimalist and clean user interface and have decided I want to dualboot with Vista.

However, I would like help installing...

I currently have 2 Local Discs (C and D) and both are NTFS and 110GB each. My Windows Vista occupies C and only has 5GB left. I have decided to use D for Ubuntu and that is completely free with 110GB of free space. In terms of partitioning, I think I am sorted and ready, although someone can clarify this as I'm not sure. 

My question is, I would like to install Ubuntu on D and keep it separate from my Vista in C. If I install via Wubi, will Ubuntu install on my C drive or can I move it exclusively to D? The reason I ask this is because when I did install Ubuntu via Wubi, I had "low disc space" after only installing 1 or 2 additional apps. I'm assuming this means that my home drive space was low. That is why I uninstalled it via Wubi and would like help installing it correctly.

Can someone (in noob terms), show me how I can install Ubuntu in my D drive, therefore separating it from my Windows in C. But I would still like to select OS when booting. I would also like to maximise usage of D and store all my music and videos there too. (which is currently worth around 60GB and I intend to expand it).  Therefore I don't want the low disc issue to arise. 

Sorry for the long winded question. If one can help someone who is potentially going to use Linux full time, then I would greatly appreciate it and would also move one away from Windows.

---

### Post by elliotcroft on 2011-05-02
There is an option to specify the partition in which Ubuntu is to be installed manually during the installation process. Select the partition that you would like it to be installed to and confirm.
I migrated to a dedicated partition from Wubi using the Wubi Move script, the instructions are [here]("http://ubuntuforums.org/showthread.php?t=1519354"). To find out what /dev/sda number the partition is, go to the partition manager on Ubuntu and look at the appropriate partition.

---

### Post by Rex Bouwense on 2011-05-02
I have a couple of references for you:
[https://help.ubuntu.com/10.04/switching/C/dualboot.html](https://help.ubuntu.com/10.04/switching/C/dualboot.html)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Mark Phelps on 2011-05-02
> **2step786 said:**
> I currently have 2 Local Discs (C and D) and both are NTFS and 110GB each. My Windows Vista occupies C and only has 5GB left. I have decided to use D for Ubuntu and that is completely free with 110GB of free space. In terms of partitioning, I think I am sorted and ready, although someone can clarify this as I'm not sure. 

My question is, I would like to install Ubuntu on D and keep it separate from my Vista in C. If I install via Wubi, will Ubuntu install on my C drive or can I move it exclusively to D? The reason I ask this is because when I did install Ubuntu via Wubi, I had "low disc space" after only installing 1 or 2 additional apps. I'm assuming this means that my home drive space was low. That is why I uninstalled it via Wubi and would like help installing it correctly.
You can not install Ubuntu natively to an NTFS partition -- you can only do that using Wubi.  And, yes, you can point Wubi to a drive other than "C:".

But, you said you wanted a non-Wubi installation...

First, you need to ensure that you do not already have the maximum of 4 primary (or 3 primary and one extended) partitions on your drive.

Second, use the Vista Disk Management utility to shrink the Vista OS partition to make room for another partition.  Do NOT use the Ubuntu installer to do that as doing it that way runs the risk of corrupting the Vista OS filesystem and rendering it unbootable.

Also, if you do not have a Vista Installation DVD, go to the link below, download and burn the proper Vista Repair CD: 

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

If you damage your Vista boot loader during dual-boot setup, you can use this Repair CD to fix it and get your Vista OS booting again.

> Can someone (in noob terms), show me how I can install Ubuntu in my D drive, therefore separating it from my Windows in C. 
Basically, you can't.  Only Wubi installs can use NTFS partitions. 

> But I would still like to select OS when booting. After you install Ubuntu to its own partition and reboot, it will only see itself.  You will then need to open a terminal and enter "sudo update-grub".  That will regenerate the GRUB menu and add an entry for Vista.

>  I would also like to maximise usage of D and store all my music and videos there too. (which is currently worth around 60GB and I intend to expand it).  Therefore I don't want the low disc issue to arise. 
Use "D" as a data drive -- do NOT install Ubuntu there.

---

### Post by Sumsi on 2011-05-23
I have a very similar question, so I thought I'd post it here instead of starting a new thread. I know nothing whatsoever about programming, so I used Wubi to install Ubuntu and be able to dual boot, because I'm not quite ready to leave windows completely (mainly for the sake of iTunes, but hey)

I have 2 hard drives on my PC, I C and D, when I first installed ubuntu via Wubi I only had 500MB of free space, which was fairly useless when I wanted to install MS office through Wine, so I de-installed ubuntu, and re-installed it (again through) Wubi deliberately selecting the D drive that has 54Gb free... however when I booted up it Ubuntu it told me I still only had 1.1gb free... 

I don't really understand why or what I have to do to sort it out, any help would be appreciated and I should probably clarify that my technical skills are virtually non-existant when it comes to PCs, so I can't do a "real" dual-boot, and I haven't the first clue about creating partitions and things! 
Thanks in advance!

---

### Post by Mark Phelps on 2011-05-24
> **Sumsi said:**
> I have a very similar question, so I thought I'd post it here instead of starting a new thread. I know nothing whatsoever about programming, so I used Wubi to install Ubuntu and be able to dual boot, because I'm not quite ready to leave windows completely (mainly for the sake of iTunes, but hey)
My responses to the original poster dealt with NOT using Wubi -- so your's is NOT the same situation.  Please start your own thread describing your problems.

> I have 2 hard drives on my PC, I C and D, when I first installed ubuntu via Wubi I only had 500MB of free space, which was fairly useless when I wanted to install MS office through Wine, so I de-installed ubuntu, and re-installed it (again through) Wubi deliberately selecting the D drive that has 54Gb free... however when I booted up it Ubuntu it told me I still only had 1.1gb free... 

I don't really understand why or what I have to do to sort it out, any help would be appreciated and I should probably clarify that my technical skills are virtually non-existant when it comes to PCs, so I can't do a "real" dual-boot, and I haven't the first clue about creating partitions and things! 
Thanks in advance!

As said, please start your own thread -- as yours is a very different problem.

---

