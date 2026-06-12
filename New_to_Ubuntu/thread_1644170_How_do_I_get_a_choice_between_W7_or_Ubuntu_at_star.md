---
title: "How do I get a choice between W7 or Ubuntu at start up?"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by Len666 on 2010-12-12
I have a HP G62 laptop with 500 gB hd.
I have shrunk my disk with 100 gB and made a new partition.
What is the simplest way to get a reliable dual boot option?
Doesn't have to be fancy, just a screen with 2 options, Windows 7 or Ubuntu 10.10.
 
Thanks for your time.
Len.

---

### Post by racie on 2010-12-12
Grub should do this for you automatically when you install Ubuntu to the unallocated space.

---

### Post by bodhi.zazen on 2010-12-12
> **Len666 said:**
> I have a HP G62 laptop with 500 gB hd.
I have shrunk my disk with 100 gB and made a new partition.
What is the simplest way to get a reliable dual boot option?
Doesn't have to be fancy, just a screen with 2 options, Windows 7 or Ubuntu 10.10.
 
Thanks for your time.
Len.

It is automatic if you install Windows first, Ubuntu second.

---

### Post by racie on 2010-12-12
> **bodhi.zazen said:**
> It is automatic if you install Windows first, Ubuntu second.

Oops, I forgot to mention that.  This is VERY important to know.

---

### Post by Quackers on 2010-12-12
Please make sure you do not try to create more than 4 primary partitions! Or 3 primarys and an extended partition. Check first.

---

### Post by Len666 on 2010-12-13
> **Quackers said:**
> Please make sure you do not try to create more than 4 primary partitions! Or 3 primarys and an extended partition. Check first.
 
Looks like you saved the day for me, Quackers... Thank you for that!
 
My W7 is OEM and is installed using recovery discs. Using these discs automatically creates 4 partitions on my disk, like a SYSTEM, a HP-TOOLS and a RECOVERY partition and leaves me the rest of the disc as my C-DRIVE, which I shrunk to get a disc to install Ubuntu on. All partitions are "Simple" and "Dynamic" but disk management doesn't say anything about being primary.
 
Is there a solution for this? 
What would happen if I install Ubuntu on this disk?
Or am I sentenced to use Ubuntu on a pendrive? I could work with that...
 
To put it mildly I'm not thrilled by the idea of removing the recovery-partition, let alone the system-partition... 
 
Thanks again for your intervention.
Len.

---

### Post by amjjawad on 2010-12-13
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)

And a lot more if you use Google or [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Good luck!

---

### Post by mastablasta on 2010-12-13
> **Len666 said:**
> Looks like you saved the day for me, Quackers... Thank you for that!
 
My W7 is OEM and is installed using recovery discs. Using these discs automatically creates 4 partitions on my disk, like a SYSTEM, a HP-TOOLS and a RECOVERY partition and leaves me the rest of the disc as my C-DRIVE, which I shrunk to get a disc to install Ubuntu on. All partitions are "Simple" and "Dynamic" but disk management doesn't say anything about being primary.
 
Is there a solution for this? 
What would happen if I install Ubuntu on this disk?
Or am I sentenced to use Ubuntu on a pendrive? I could work with that...
 
To put it mildly I'm not thrilled by the idea of removing the recovery-partition, let alone the system-partition... 
 
Thanks again for your intervention.
Len.
 
 
i don't think it will be a problem (especially if windows works nicely now).
 
to see which partition are primary (obviously MS has new terminology now) you can use gparted via live session (just type sudo gparted in temrinal when in live session). it will tell you which ones are primary and such. as long as you don't make and then apply any changes, it won't mess up your disk. 
 
Linux can be installed on extended partition. but Windows must have primary one.
 
sorry i can't help you more as i am still on WinXP.

---

### Post by Quackers on 2010-12-13
If they are now shown as SFS volumes it is likely that Linux systems won't see them. I fear my message came a little late. 
It is possible to change them back to basic but it is quite a bit of work and carries risks. I believe amjjawad posted some links on the subject. Good luck!

---

### Post by Jakey_TheSnake on 2010-12-13
I'd just remove HP Tools if I were you. 

HP install lots of unnecessary crap on your laptop, if I did buy one I'd wipe the drive anyway and use a clean copy of Windows. Unless you're running without an anti-virus/firewall or are downloading ViRuS.JPG.exe I highly doubt you'll need any of their system restore tools. 

Note: I think Ubuntu can be installed on a Logical partition? But those have to be created inside an extended partition, which counts as a primary so you'd have to remove one to create it anyway.

---

### Post by amjjawad on 2010-12-13
> **Jakey_TheSnake said:**
> HP install lots of unnecessary crap on your laptop, if I did buy one I'd wipe the drive anyway and use a clean copy of Windows. 

A lot will disagree with you about that. IMHO, these stuff (or crap as per your post) are there for a reason.

> I highly doubt you'll need any of their system restore tools. 

You never know what could happen.

> Note: I think Ubuntu can be installed on a Logical partition? 
Yes, it does.

---

### Post by amjjawad on 2010-12-13
> **Len666 said:**
> My W7 is OEM and is installed using recovery discs. Using these discs automatically creates 4 partitions on my disk, like a SYSTEM, a HP-TOOLS and a RECOVERY partition and leaves me the rest of the disc as my C-DRIVE, which I shrunk to get a disc to install Ubuntu on. All partitions are "Simple" and "Dynamic" but disk management doesn't say anything about being primary.
 
I've never had to do it before but I guess you could burn the content of these partitions to a disk (CD/DVD).
Anyway, if you have Ubuntu's LiveCD, try to boot your machine (don't forget your BIOS settings - CD-Drive must be first) and run GParted (System > Administration > GParted) and have a look at your partitions. Don't change anything though, just have a look. *Disc Manager in Windows must say whether these partitions are Primary or not but I'm not 100% sure about that.* I don't have a laptop to check that.

> What would happen if I install Ubuntu on this disk?
Or am I sentenced to use Ubuntu on a pendrive? I could work with that...
 
Do you have an external HDD? you could keep everything as it's and install Ubuntu there. Just a thought. You might not like it but it's just a thought.


> To put it mildly I'm not thrilled by the idea of removing the recovery-partition, let alone the system-partition... 
 
As I mentioned early, if it's possible to burn that on CD/DVD, then it's good idea.

---

