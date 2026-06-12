---
title: "[SOLVED] can not create folder  folder inside '/' (Filesystem)"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by mrprajesh on 2009-01-09
when i installed Ubuntu 8.04 ..
i have allocated 3 GB for /home and 15 GB for '/' :D
in my hp pavilion Desktop ( pre-installed with XP) :D

i was saving files only inside Documents (naturally /home), Now *i m in need to store more file*s so i thought of creating folder inside / . but i m not able to do as that option is disabled:(

i have also tried to login as root. but that is also not allowed:confused:

am i proceeding the right way ? :confused:
i m new to ubuntu. adv thanks for ur replies !:D

---

### Post by nothingspecial on 2009-01-09
You shouldn`t need to create files inside root.

If you do they will all be owned by root and that will lead to an awful lot of sudoing and probable breakage if you don`t know what your doing.

---

### Post by amauk on 2009-01-09
you're going to have to increase the size of your /home partition

boot into a LiveCD
and use the partition editor (gparted)
reduce the root (/) partition - say, to 8Gb

use the free space to expand your home partition

---

### Post by lazyart on 2009-01-09
Your better bet would be to use GParted from the live CD and resize your partitions.  You don't want to be storing stuff on /.

Resizing partitions could cause you to lose data (a power outage would be problematic) so backup your data before embarking.

Shrink / by a couple gigs, then expand /home to take advantage of it.  Or if possible give up some free space from your Windows partition to accomodate.

Root login in disabled in Ubuntu.  And no, we don't dicuss how to enable it here so don't even ask.

---

### Post by nothingspecial on 2009-01-09
> **amauk said:**
> you're going to have to increase the size of your /home partition

boot into a LiveCD
and use the partition editor (gparted)
reduce the root (/) partition - say, to 8Gb

use the free space to expand your home partition


Make sure you know exactly what you`re doing before messing with your partitions. Risk of mass data loss. Please back up first.

---

### Post by mrprajesh on 2009-01-09
>  Originally Posted by amauk  View Post
you're going to have to increase the size of your /home partition

boot into a LiveCD
and use the partition editor (gparted)
reduce the root (/) partition - say, to 8Gb

use the free space to expand your home partition

Make sure you know exactly what you`re doing before messing with your partitions. Risk of mass data loss. Please back up first.

oh this seems serious. then should i reinstall ubuntu again or just resizing /home will sove my prob? if so how to do that (can i do resizing of with Ubuntu live CD)?

....i understand that only /home is used for saving user's file. so when ever installing ubuntu one should alocate (equally )more space to /home than '/'. May b in my case i should hav used aleast 10GB for /home &  8 gGB for '/'

---

### Post by amauk on 2009-01-09
it's not that serious
problem is, you can't resize partitions if they're in use, so you have to do it "outside" your operating system (IE. using a LiveCD)

the partition editor is an easy graphical app

---

### Post by Captain_tux on 2009-01-09
Serious? Yes... it can lead to data loss.

Difficult? No. Just pay attention as you're using **GParted**, **QtParted** or whatever your preferred partitioner is.

---

### Post by mrprajesh on 2009-01-09
> it's not that serious
problem is, you can't resize partitions if they're in use, so you have to do it "outside" your operating system (IE. using a LiveCD)

the partition editor is an easy graphical app

Any how i had to back my files in ubuntu to windows for resizing...so thought of formating and installing ubuntu again with Intrepid Ibex (8.10) :D
thanx all !

---

### Post by mrprajesh on 2009-01-09
> Serious? Yes... it can lead to data loss.

Difficult? No. Just pay attention as you're using GParted, QtParted or whatever your preferred partitioner is.
thnx any way..i hav chosen the path that i know to do :D
i havnt used gpated (its need creating Live CDs, booting it with ,resiziing -all that i havn't done )i dont want to risk too much. :D

---

### Post by Captain_tux on 2009-01-09
> **mrprajesh said:**
> thnx any way..i hav chosen the path that i know to do :D
i havnt used gpated (its need creating Live CDs, booting it with ,resiziing -all that i havn't done )This may crash grub preventing me to enter winDoz. i dont want to risk too much. :D

Fair enough. Let us know how you do... if you run into any problems, re-post!

---

### Post by nothingspecial on 2009-01-09
Sometimes that`s the best option.

I`m cautious when I give help because I have suffered mass data loss.

One day when an opportunity presents itself get an old virused laptop that nobody wants anymore, install linux on it and break it as much as you can, that way you`ll learn. Don`t try risky stuff on your main system.

---

### Post by mrprajesh on 2009-01-09
> One day when an opportunity presents itself get an old virused laptop that nobody wants anymore, install linux on it and break it as much as you can, that way you`ll learn. Don`t try risky stuff on your main system.
This sounds cool !! i 'll try in future..

---

