---
title: "grub not loading and on fdisk -l from live cd returns nothing"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by thehaltingproblem on 2010-07-21
Hi,

I have been using ubuntu 9.04 for about 2 months now. I ran into a problem yesterday. I run a windows XP - ubuntu 9.04 dual boot. Yesteraday, my computer became real slow, and I had to restart it 4-5 times, after which, the package manager had some errors, and when I restarted it again, it wanted me to do fsck manually. But fsck never got over, it always got stuck at some point, and after some more restarts, I have started getting blank screens, and even grub wouldn' load.
I tried the live cd, and did fdisk -l from the terminal and it returned nothing. Can someone helpe me out?
Btw, if it helps, just before I logged in through live cd, it said grub error 16.

Thanks in advance.

---

### Post by Sef on 2010-07-21
> I tried the live cd, and did fdisk -l from the terminal and it returned  nothing. Can someone helpe me out?Try ```
sudo fdisk -l
```  Just copy and paste the code.

---

### Post by thehaltingproblem on 2010-07-21
> **Sef said:**
> Try ```
sudo fdisk -l
```  Just copy and paste the code.
I did sudo fdisk -l last time as well and just to be sure did it again, but still doesn't return anything! :(

---

### Post by ranch hand on 2010-07-21
When you are on your Live CD and you open nautilus can you see any of your files, Ubuntu or MS?

What does gparted show?

You can install programs when in the Live session.  They just load on your ram and work from there and are gone when you reboot.  You may want to try testdisk on your partitions if you can find them.

It could be that your HDD just went south.  If so you may be able, if the nautilus in the Live session can see the files, to recover some that way.

---

### Post by warfacegod on 2010-07-21
You might consider cleaning your computer for dust.

Also, running memtest would be wise. I can't remember if you can run that from a LiveCD though.

---

### Post by ranch hand on 2010-07-21
I run with my box open so it gets cleaned very regularly.  I always forget about it as a problem.  I can of air is your friend. 

Another thing you might do is to unplug your HDD and plug it back in a couple of times (Power off and box unpluged).  Could be dirty connections.

---

### Post by warfacegod on 2010-07-21
memtest can be run from the GRUB LiveCD.

---

