---
title: "location of swap partition"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by jotiho on 2010-01-24
I am running 9.04 from a small (3.8 GiB) drive, and have just added a 30GiB drive.  At the moment, the whole of the new drive is assigned to a single partition mounted at /home.  My system has 0.5 Gb RAM and a swap partition  of only 0.235 GiB located on the small drive.  

My ( double) question is, 

  -  is it possible to put the swap partition on the second drive (where it could be give  more space); and
  -  would this be a better set-up?  (For example allowing for hibernation)

Thanks for any suggestions

John

---

### Post by NCLI on 2010-01-24
Yes and yes :)

---

### Post by mbzn on 2010-01-24
Yes and yes. just create a swap partition on the larger drive(recommended is 2xthe amount of memory) 1gig swap and activate(you'll have to read up on that, i cant remember).
remember you'll have to shrink you /home partition which can cause data-loss so backup,backup,backup... resizing can be done in gparted.

Good luck

---

