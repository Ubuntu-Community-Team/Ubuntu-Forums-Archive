---
title: "Dual-Boot with Win7?"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by Niu Garzukk on 2010-03-21
I'm interested in dual booting my laptop with Ubuntu. I run 32bit Win7 OS with 3GB RAM, 120 HD (about 80 left) and a  2.1Ghz Intel Centrino Dual-Core Processor. This laptop was originally shipped with Win Vista Premium but I received a free upgrade to Win7 when it was released. 

Thanks for the help,
Niu

---

### Post by _h_ on 2010-03-21
Ubuntu Community Help section guide for dual booting Windows and Ubuntu:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Has instructions on how to do so. Good luck. :)

---

### Post by gjoellee on 2010-03-21
If you have Windows installed, you pretty much just chose to install Ubuntu next to Windows, and you should be able to dual boot without further problems.

---

### Post by oldfred on 2010-03-21
In the instructions linked above on resizing 

**[B][SIZE=1]Windows Vista and Windows 7[/SIZE]**[/B]

 The Windows partition must be resized from *within* Windows Vista and Windows 7 using the shrink/resize option: Do not use gparted.

Resize your windows and reboot several times to make sure it has done its checkdisk or other repairs before installing Ubuntu.

---

### Post by sandyd on 2010-03-21
> **oldfred said:**
> In the instructions linked above on resizing 

**[B][SIZE=1]Windows Vista and Windows 7[/SIZE]**[/B]

 The Windows partition must be resized from *within* Windows Vista and Windows 7 using the shrink/resize option: Do not use gparted.

Resize your windows and reboot several times to make sure it has done its checkdisk or other repairs before installing Ubuntu.

Fixed. Check the wiki page again ;)

---

### Post by Mark Phelps on 2010-03-22
Carlee:

Like the recent change to the Wiki:

```
NOTE: DO NOT RESIZE WINDOWS 7 / VISTA PARTITIONS USING THE UBUNTU PARTITONER. RESIZE THEM USING THE WINDOWS PARTITION MANAGER. 
```

Now ... if we could only get folks to stop telling people to simply do a side-by-side, we would be OK.

---

### Post by cap10Ibraim on 2010-03-22
I did that before but then I realized how annoying is dual booting so I installed ubuntu on the whole  hard disk and windows 7 on the VirtualBox

---

### Post by sandyd on 2010-03-22
> **Mark Phelps said:**
> Carlee:

Like the recent change to the Wiki:

```
NOTE: DO NOT RESIZE WINDOWS 7 / VISTA PARTITIONS USING THE UBUNTU PARTITONER. RESIZE THEM USING THE WINDOWS PARTITION MANAGER. 
```

Now ... if we could only get folks to stop telling people to simply do a side-by-side, we would be OK.

thanks! :)

---

### Post by ubu newb on 2010-03-22
> **Mark Phelps said:**
> Carlee:

Like the recent change to the Wiki:

```
NOTE: DO NOT RESIZE WINDOWS 7 / VISTA PARTITIONS USING THE UBUNTU PARTITONER. RESIZE THEM USING THE WINDOWS PARTITION MANAGER. 
```Now ... if we could only get folks to stop telling people to simply do a side-by-side, we would be OK.


[COLOR=Navy] Wish I would have seen this before I did side by side. :-x    I re-sized through Ubuntu a small section.  But I also had no choice since I had no access to Windows 7.

Is there away to fix that other than re-format and re-install both OS's?[/COLOR]

---

### Post by OneHero on 2010-03-22
> **ubu newb said:**
> [COLOR=Navy] Wish I would have seen this before I did side by side. :-x    I re-sized through Ubuntu a small section.  But I also had no choice since I had no access to Windows 7.

Is there away to fix that other than re-format and re-install both OS's?[/COLOR]

Put in your Windows XP recovery disk.

---

### Post by Mark Phelps on 2010-03-22
> **OneHero said:**
> Put in your Windows XP recovery disk.

Windows XP disk can NOT fix Win7 -- or didn't you bother to actually read what the OP was asking.

---

### Post by Mark Phelps on 2010-03-22
> **ubu newb said:**
> [COLOR=Navy] Wish I would have seen this before I did side by side. :-x    I re-sized through Ubuntu a small section.  But I also had no choice since I had no access to Windows 7.

Is there away to fix that other than re-format and re-install both OS's?[/COLOR]

Fix what?  You haven't told us what the problem is yet.

Win7 can be repaired (if boot failure is the problem) using a Win7 Repair CD, the image of which can be downloaded from the NeoSmart Technology forums at the following location:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by ubudog on 2010-03-22
Shouldn't be a problem.  This may help with it: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by sandyd on 2010-03-22
> **ubudog said:**
> Shouldn't be a problem.  This may help with it: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

eh.
should be 
[https://help.ubuntu.com/community/RecoveringWindows#Resizing Windows Vista / 7 Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing Windows Vista / 7 Partitions)

instead.

---

### Post by ubudog on 2010-03-23
> **carlee said:**
> eh.
should be 
[https://help.ubuntu.com/community/RecoveringWindows#Recovering After Resizing Windows Vista / 7](https://help.ubuntu.com/community/RecoveringWindows#Recovering After Resizing Windows Vista / 7)

instead.

Whoops.

---

### Post by sandyd on 2010-03-23
> **ubudog said:**
> Whoops.

fyi, I wrote that right after you posted the dual boot link :D

peace.:KS

---

