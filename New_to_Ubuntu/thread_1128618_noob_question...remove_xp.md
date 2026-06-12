---
title: "noob question...remove xp"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by drdave69 on 2009-04-17
I am trying to remove all xp stuff from my computer. I have a few storage drives that have the ntfs file system on them, i want to change it to the ubuntu file system. how do i do this?

---

### Post by NESFreak on 2009-04-17
you could use Gparted. It's in synaptic. Its also on the live CD. You can even use it to make your linux partition fit your harddrive (resize a partition), after removing the windows partitions.

--removing windows is quite a radical thing to do for a newbie, are you sure you can handle it? If you dont need the space right now, id say leave it this way. It might once save you. (you can even use gparted to make your windows partition smaller, without removing it.

---

### Post by coffeeaddict22 on 2009-04-17
If you change the filesystem, you'll lose the data unless you've backed it up/ moved it first.  Linux will happily work with your ntfs partitions, and there are benefits in keeping all your old data in one place unless you're one of those organised people...

 It's also considered good practice to put your Linux system files in a separate partition to the /home filesystem (ie all your data files), so moving all the other stuff is only of minimal benefit in more than one way.

---

### Post by lisati on 2009-04-17
Make sure you don't accidentally clobber your recovery partition (if your machine has one), "just in case".

---

### Post by trlkly on 2009-04-17
Yeah. I hosed my recovery partition. Had to find a regular WinXP CD to reinstalll, and then hunt down drivers. Not fun.

(If you're wondering: Sis wants to play the Sims 2)

---

### Post by drdave69 on 2009-04-18
> **NESFreak said:**
> you could use Gparted. It's in synaptic. Its also on the live CD. You can even use it to make your linux partition fit your harddrive (resize a partition), after removing the windows partitions.

--removing windows is quite a radical thing to do for a newbie, are you sure you can handle it? If you dont need the space right now, id say leave it this way. It might once save you. (you can even use gparted to make your windows partition smaller, without removing it.
I installed Gparted, but can not find it anywhere on my computer. Can anyone tell me how to use this program?
Thanks in advance, Dave

---

### Post by Toshubu on 2009-04-18
System > Administrator > Partition Editor...(Is it not there?)...

---

### Post by drdave69 on 2009-04-18
> **Toshubu said:**
> System > Administrator > Partition Editor...(Is it not there?)...
Thanks...its there....was looking for "Gparted" not "Partition Editor" sorry for such a noob mistake LOL

---

### Post by Toshubu on 2009-04-18
That's exactly what happened to me...

---

