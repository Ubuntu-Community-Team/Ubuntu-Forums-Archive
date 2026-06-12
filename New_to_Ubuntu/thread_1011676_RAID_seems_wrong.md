---
title: "RAID seems wrong"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-12-15
I setup a RAID 0, but when my system POSTs it says my HDD is 1TB. Isnt this wrong if I have 2 500GB HDD? I though it splits data to both drives, to create greater throughput  and the "Hard Drive" that the system sees is 1 500GB drive.

---

### Post by shifty_powers on 2008-12-15
no that is correct.

raid 0 splits the data between drives, striped, to give a boost in performance, as it is using both at once, so that data throughput is increased. Of course this means that if one drive fails then you loose all data. It also means that you will get the capacity of both drives, in this case giving you 1TB of space.

Raid 1 is where the data is copied, or mirrored, between the two drives. This creates an exact copy of the data, meaning that if one drive fails, all the data is safe. This is redundancy. It also means that you "loose" the capacity of one drive, in this case giving you 500GB of space.

You seem to want the performance of Raid 0 with the redundancy of Raid 1. You do get things like Raid 10 which will go in that direction, but you need more than 2 drives.

I think you need to read up on Raid...

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

---

### Post by Kellemora on 2008-12-15
Unless your RAID controller goes south, then you've lost everything also!  Because it's nearly impossible to find an IDENTICAL RAID controller to the one you bought last year or the year before.  Raid Controllers are NOT plug n pray, they must be the exact controller that set up the Raid, not the version before or after it either.

You are better off simply mirroring one drive to the other using the drives own controllers to take care of the file system.

The data you save may be your own!

TTUL
Gary

---

