---
title: "Dual boot memory share"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2010-07-18
Hi guys, could anyone please let me know if there is an easy way to transfer memory between my 2 operating systems and the shared memory?
I have 15 Gigs in windows 7. 10 gigs in the shared and only 1,6 in Linux which is the one I use the most! I only use windows for syncing my gadgets! and don,t need all that memory in the shared!
It would be great if I could move about 5 or more gigs from either of the other 2 into my Linux memory!

please help

---

### Post by ron999 on 2010-07-18
Hi
Boot from the Ubuntu LiveCD and use gParted Partition Manager.
It's probably located at Systems > Administration > Partition Manager.

---

### Post by Mark Phelps on 2010-07-18
> **cheekymonky2010 said:**
> Hi guys, could anyone please let me know if there is an easy way to transfer memory between my 2 operating systems and the shared memory?
I have 15 Gigs in windows 7. 10 gigs in the shared and only 1,6 in Linux which is the one I use the most! I only use windows for syncing my gadgets! and don,t need all that memory in the shared!
It would be great if I could move about 5 or more gigs from either of the other 2 into my Linux memory!

please help

First of all, it's not MEMORY, it's DISK SPACE.

Second, do NOT use GParted to shrink the Win7 partition.  That runs the risk of corrupting the OS and rendering it unbootable.  Use the Win7 Disk Management utility to shrink the Win7 partition.

Third, you will NOT be able to resize the Ubuntu partition when running Ubuntu because you'll be using that very partition.  Download and burn a GParted LiveCD from distrowatch.com, boot from that, and use that to resize the Ubuntu partition.  And be patient... GParted can take a LONG time to reize partitions.  If you get impatient and halt it before it finishes, it will corrupt your filesystem and most probably, require a complete reinstall of Ubuntu to get it back to working order.

---

### Post by cheekymonky2010 on 2010-07-18
That sounds pretty intimidating because I am very new to Ubuntu and would not want to lose it all together!   the main reason is that I tried to burn a dvd to watch on my dvd player and it says that it needs 4,8 gigs of disk space and there was only the 1,6 in Ubuntu!  
Is there another way to burn the dvd?

---

### Post by Mark Phelps on 2010-07-18
> **cheekymonky2010 said:**
> That sounds pretty intimidating because I am very new to Ubuntu and would not want to lose it all together!   the main reason is that I tried to burn a dvd to watch on my dvd player and it says that it needs 4,8 gigs of disk space and there was only the 1,6 in Ubuntu!  
Is there another way to burn the dvd?

Not that I know of...

If you write the DVD stuff to your Win7 partition, then you will have to mount it read-write, which is generally not a good idea.

---

