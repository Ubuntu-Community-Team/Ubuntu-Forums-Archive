---
title: "multi OS/boot question (4+)"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by wizehawk on 2009-01-26
i currently have a 320gb hard drive, and wanted to install the following operating systems
ubuntu 9.06
ubuntu 8.10
windows vista
windows 7 beta

i was wondering if somebody would help me out in what should be a good partition set up for all the os'es, and if doing a quadruple-boot os is a very bad idea? and why?
how significant is the amount of operating systems on slowing down the boot time?
whats the maximum of os'es that grub can handle?

EDIT: can you even run two different version of ubuntu on the same hard drive (different partitions)

---

### Post by lswb on 2009-01-26
Check [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 

The setup you want is not too difficult. My old laptop has windows XP, dapper, and hardy all installed on an 80GB drive as well as a shared data partition.

---

### Post by -kg- on 2009-01-26
> how significant is the amount of operating systems on slowing down the boot time?

The answer to this question is: None.  You can only boot one OS at a time, so the speed will be dependent on how you have that particular OS set up and configured.

---

### Post by BDNiner on 2009-01-26
The setup you desire would not be hard to accomplish. you should not have any performance issues since you only boot one OS at a time. I personally would setup Windows 7 and 9.06 in virtual machines since you may not be able to get drivers and they are not stable yet.

---

### Post by candtalan on 2009-01-26
I believe that it is easiest by installing Windows on the drive first, then ubuntu.
Which ever ubuntu you install last of all, will end up controlling the whole boot sequence, using grub, as I understand it.

I have no idea how you should best install the two windows' versions, or what advantages with installing which Windows first or second. I guess that at that stage you will be using a Windows boot manager. I have no experience about that.

After install of the first Ubuntu, you should see grub has picked up both windows and also the ubuntu. Then after the second Ubuntu install its grub should take over afresh, both windows and both Ubuntu's.

I believe that each windows will need to be installed into its own partition. You might like to consider using a manual (non automatic) method of install of the ubuntus, although checking the suggested automatic install options might be ok with ubuntu.

Check out the intended partition count - one each for windows, and (nominally) two each for the Ubuntus. You could arrange for the Ubuntus to share a single swap partition if you wanted, but it will not be too important.

Unless you do it first, the first Ubuntu install will create an extended partition containing two more, logical, nominally partitions 5 and 6. The last Ubuntu install will need two more partitions, and will try to create them semi automatically, I cannot predict exactly what it will try to create, or what might possibly go wrong(?) It is the final Ubuntu install that will need the most partition understanding or planning.

I usually use 'parted magic' live CD or something similar to examine and change partitions.

HTH

---

### Post by kansasnoob on 2009-01-26
> **wizehawk said:**
> i currently have a 320gb hard drive, and wanted to install the following operating systems
ubuntu 9.06
ubuntu 8.10
windows vista
windows 7 beta

i was wondering if somebody would help me out in what should be a good partition set up for all the os'es, and if doing a quadruple-boot os is a very bad idea? and why?
how significant is the amount of operating systems on slowing down the boot time?
whats the maximum of os'es that grub can handle?

EDIT: can you even run two different version of ubuntu on the same hard drive (different partitions)

First of all I know nothing about Win 7 (and I don't plan on wasting time on it), but Win being Win I would find a dual boot guide for Vista and Win 7! Hopefully that guide would allow you to use no more than 3 (preferably 2) Primary partitions.

You see there is a 4 primary limit on all drives! So you could have Win 7 on one Primary, Win Vista on another Primary, and then you could still have room for one Primary for your first Linux OS (just in case you decide to ditch Win altogether), and then you could build an almost endless number of logical partitions within the last extended partition.

---

### Post by bodhi.zazen on 2009-01-26
To answer the OP question, it should work just fine, the only problem is configuring your system to boot.

On these forums, for the most part, we use grub. Alternately you can configure the windows boot loader to do this, but you will find less support for that here.

To start with , partitioning.

I suggest :

primary - Vista
primary - Windows 7
primary - NTFS shared data drive

Extended
logical - Ubuntu 8.04
logical - Ubuntu 9.04
swap

If you do not understand partitioning see : 

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

Install vista, Windows 7 , 8.10, then 9.04 (Alpha 3 )

Last configure grub :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817") 

The only problem you may have is with windows, you have to "hide" the windows partitions from each other.

See : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

and for multi-windows : [http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_)

If you wish to use the windows boot loader see :

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

The last link was found with a simple google search using the following search criteria ;

> multiboot windows XP + vista + Ubuntu

---

### Post by wizehawk on 2009-01-27
thanks for you all your help, ill try it out once i get home tonight....

haha just for fun... is it possible to force a mac osx on a windows pc (intel proccessors core 2 duo processors)

---

### Post by igknighted on 2009-01-27
> **wizehawk said:**
> thanks for you all your help, ill try it out once i get home tonight....

haha just for fun... is it possible to force a mac osx on a windows pc (intel proccessors core 2 duo processors)

Possible?  In some cases, yes (if you get a hacked version).  However it is against the EULA and illegal, even if you have legally bought the software.

---

