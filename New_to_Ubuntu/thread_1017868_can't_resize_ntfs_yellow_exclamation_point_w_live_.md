---
title: "can't resize ntfs yellow exclamation point w/ live cd gparted dual boot"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by josephpford on 2008-12-21
I have just reinstalled windows and want to dual boot ubuntu.  I booted up a fresh live CD and opened System -> Admin -> Partition Editor (gparted).

The dev/sda1 ntfs drive has a yellow exclamation point.  I did defrag windows before booting to Ubuntu Live CD.  

When I click the ntfs partition (dev/sda1) and then click Resize/Move the Minimum and Maximum sizes are identical, and I can't resize at all.

Windows is using about 12G, I want to allocate:

30G ntfs
180G ntfs (Shared Data drive)
30G ext2/ext3 Ubuntu

How do I resize?

I've tried sudo gparted, no luck...

Thanks!
Joe

---

### Post by josephpford on 2008-12-21
Also - I tried starting Partition Editor with and without Mounting the NTFS file system.

Thanks!


> **josephpford said:**
> I have just reinstalled windows and want to dual boot ubuntu.  I booted up a fresh live CD and opened System -> Admin -> Partition Editor (gparted).

The dev/sda1 ntfs drive has a yellow exclamation point.  I did defrag windows before booting to Ubuntu Live CD.  

When I click the ntfs partition (dev/sda1) and then click Resize/Move the Minimum and Maximum sizes are identical, and I can't resize at all.

Windows is using about 12G, I want to allocate:

30G ntfs
180G ntfs (Shared Data drive)
30G ext2/ext3 Ubuntu

How do I resize?

I've tried sudo gparted, no luck...

Thanks!
Joe

---

### Post by josephpford on 2008-12-21
I figured it out!

I right clicked the drive and choose "Information" and saw the attached.

Sorry for the unneeded question!

~Joe



> **josephpford said:**
> Also - I tried starting Partition Editor with and without Mounting the NTFS file system.

Thanks!

---

### Post by Captain_tux on 2008-12-21
Well done!

---

### Post by mkvnmtr on 2008-12-21
It wasn't an unneeded question, I learned something. 
Boy that GParted is some fine piece of work.

---

### Post by caleb.gross on 2008-12-21
I have the same yellow exclamation point, but a different problem. What do you make of this? 
I'm trying to create a dual-boot with xp pro and intrepid


*the bottom was cut off, I couldn't position the window any higher to get the rest of the message

---

### Post by Pedro D on 2009-04-02
Wow thank you that solved my problem :D

---

