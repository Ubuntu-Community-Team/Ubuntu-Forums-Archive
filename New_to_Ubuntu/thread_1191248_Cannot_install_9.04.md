---
title: "Cannot install 9.04"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by stlcity on 2009-06-18
I tried multiple times to install 9.04 into my desktop as dual boot into windows vista. The installation goes fine. Ubuntu shows up in the initial boot menu. When I chose Ubuntu I get the black screen with the following error message:

Try(hd0,0): NTFS5: No wubildr
Try (hd0, 1): Extended:
Try (hd0,2): Ext2:_

I cannot type anything and have to do a hard boot to restart again. Any suggestions?

---

### Post by LewRockwell on 2009-06-18
wonder why you're getting any message related to wubi when you are doing a dual-boot installation?

---

### Post by Clorow on 2009-06-18
Wubi is a dual-boot installation, it's just not dual-partition.

So are you installing with Wubi, or with the CD? Wubi is good for trying Ubuntu, but not for long-term use.

---

### Post by Torgas Prim on 2009-06-18
See if you have your disk set to "Dynamic" in the disk editor.
If it is you cannot install another os on it.

---

### Post by stlcity on 2009-06-19
> **Clorow said:**
> Wubi is a dual-boot installation, it's just not dual-partition.

So are you installing with Wubi, or with the CD? Wubi is good for trying Ubuntu, but not for long-term use.

I burnt the iso image from the website and used the CD i made to try and install it. I know that the cd works because I used the same CD to install ubuntu in my HP laptop and it worked fine...not sure what to do.:(

---

### Post by stlcity on 2009-06-19
> **Torgas Prim said:**
> See if you have your disk set to "Dynamic" in the disk editor.
If it is you cannot install another os on it.

When I check under program files on the C drive I do have Ubuntu listed on there. I am thinking that it is installing okay but for some reason it stalls at the boot stage. Cannot figure it out. 

The error message keeps quoting HD0 which if I look under windows is not the drive with the OS on it. THe C drive that is my main HD is listed as HD1. Confused....

---

### Post by wpshooter on 2009-06-19
> **stlcity said:**
> I burnt the iso image from the website and used the CD i made to try and install it. I know that the cd works because I used the same CD to install ubuntu in my HP laptop and it worked fine...not sure what to do.:(

When you attempted to install Ubuntu were you **IN** the Windows operating system or did you attempt the install at the BOOT level by having the CD in the computer when you booted it ?

It almost sounds like to me that Ubuntu was installed from within Windows.

---

### Post by candtalan on 2009-06-19
> **stlcity said:**
> When I check under program files on the C drive I do have Ubuntu listed on there.

This is what you would see if you installed by putting the CD into a running windows system and (using wubi) installed - you would see a Ubuntu folder within Windows when you ran Windows.

>  I am thinking that it is installing okay but for some reason it stalls at the boot stage. Cannot figure it out 

sounds a bit like that maybe

> 
The error message keeps quoting HD0 which if I look under windows is not the drive with the OS on it. THe C drive that is my main HD is listed as HD1. Confused....

Drive names in some systems begin at zero not one, so the first drive could be drive zero, and in a more human friendly notation this would actually be drive 'one'.

*If* you have installed using wubi, into Windows, then the boot loader which is used is the Windows boot loader, not a linux boot loader. You would initially see a very simple choice between Windows (the default) and Ubuntu. 

If you chose ubuntu then there may then be a brief message about the esc key (if used it would I think reveal another menu, (grub?) not sure?).

hth

---

### Post by candtalan on 2009-06-19
> **stlcity said:**
> I tried multiple times to install 9.04 into my desktop as dual boot into windows vista. The installation goes fine.
Just a thought - after the first install, failed or partial success or whatever, either from wubi (into windows) or into a new partition proper, I wonder what action did you take to clean up or uninstall or remove partitions (if relevant)??

It is jus t that after a partial install under some circumstances you might need to make careful preparation to install again. The automatic installer will not do much cleaning up for you, it may assume that the disk or system is full of systems you need to keep.

---

