---
title: "Running installer"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by AtariRaccoon on 2009-09-20
Okay, I think I've missed something here (of course).  Trying to get Wubi to even run on my Win98se machine.  Of course, double click, things happen, some process go, hard drived is checked... then nothing.  The processes even end so I think I may have failed the memory check.

What I WANT to do is dual boot Ubuntu (and install as well) with my win98 machine.  Though I may believe that due to my win boot being on a half full 6gig drive, I don't think the program will run.

Is it actually possible to dual boot it with both OS's on seperate drives (oh yeah the other drive is of a 20gig variety), or should I just buckle down and reinstall windows and all those dang drivers again onto my larger capacity drive. x.x

---

### Post by Paqman on 2009-09-20
Do you know what filesystem your Win98 partition is in? If it's FAT32 you could have trouble, you'd be limited to a 4GB virtual disk size, which is a bit too small really.

---

### Post by AtariRaccoon on 2009-09-20
Actually yes, it is running on a fat32 system.... hummm... starting to sound like I should move my spare files over from my larger drive, reformat it with a fat 16 format(?) then reinstall win98 on that and hope Wubi will do it's magic on that side?

---

### Post by louieb on 2009-09-20
> **AtariRaccoon said:**
> 
Is it actually possible to dual boot it with both OS's on seperate drives (oh yeah the other drive is of a 20gig variety), 

Not a problem Linux on one drive - something else on the other. 20GB hard drive space is plenty.  How much ram does it have? 384MB is the minimum recommended.

---

### Post by Windows Nerd on 2009-09-20
Additionally, if your disk is more than half full on a 6 Gb drive, Wubi may not work because Ubuntu needs about 4 Gigs of space for a clean, new install. I recommend using Ubuntu on the 20 Gig drive -> It is plenty of space.

Scott

---

### Post by Paqman on 2009-09-20
> **AtariRaccoon said:**
> Actually yes, it is running on a fat32 system.... hummm... starting to sound like I should move my spare files over from my larger drive, reformat it with a fat 16 format(?) then reinstall win98 on that and hope Wubi will do it's magic on that side?

Any FAT filesystem is going to have the same limitation. I'd suggest using the conventional installer rather than Wubi, and install Ubuntu onto it's own partition.

---

### Post by AtariRaccoon on 2009-09-20
btw, if I do install it onto another hard drive while letting the boot installer on the CD create the dual boot, I noticed that it wanted to make a seperate partition on the 20g drive.  Would that actually delete everything on the drive (I have doubts but I sure ain't gonna loose personal data un-backed up.)

---

### Post by Paqman on 2009-09-21
You can tell the installer how much space you'd like it to use. It's quite capable of shrinking existing partitions to create room for the new ones it'll create.

---

