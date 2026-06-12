---
title: "Reinstall Windows XP with Recovery Disks... wll it erase Ubuntu?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by the8thstar on 2009-01-23
Well folks the title says it all.

I kept the Recovery disks from when I had Windows XP running on my computer. I ditched XP a long time ago and now I solely run Ubuntu 8.10.

I want to use the Recovery disks to reinstall Windows XP alongside Ubuntu (each on its own partition of course).

But I wonder if the recovery disks will wipe out Ubuntu in the process. What do you guys think? Have any of you tried this before?

---

### Post by Therion on 2009-01-23
I can just about guarantee you the Recovery Disk will do exactly that.

Your best bet, for clean installs all the way around, would be to install Windows XP and then install Ubuntu.  

You CAN do it the other way around, I just don't suggest it.  Google'ing "Dual Boot XP and Ubuntu" should get you started on the path.

---

### Post by XanderCrews on 2009-01-23
If your windows needs aren't too heavy, you could try a program like virtualBox or VMWare.

---

### Post by SunnyRabbiera on 2009-01-23
I would suggest a backup in any case, XP is a computer hog and it demands all space so I would just back things up.
Or use VB

---

### Post by thomas228 on 2009-01-23
> **the8thstar said:**
> Well folks the title says it all.

I kept the Recovery disks from when I had Windows XP running on my computer. I ditched XP a long time ago and now I solely run Ubuntu 8.10.

I want to use the Recovery disks to reinstall Windows XP alongside Ubuntu (each on its own partition of course).

But I wonder if the recovery disks will wipe out Ubuntu in the process. What do you guys think? Have any of you tried this before?

Hi
When I installed Ununtu the first time I messed up and had to reinstall windows,

Heres what worked for me.

Use gpartded to move ubuntu and its dirs to the end of the drive.

A backup might be in order but I was lucky and my moved ubuntu still worked fine.

The smallest partition size I could use was around 13 GB for the windows XP installation.  I formatted that first partition as NTSF.

The recovery disks worked fine for installing windows XP however I had to reinstall grub and correct menue.lst

Other than that everything worked fine for both XP and Ubuntu8.04

Good luck

Tom

---

