---
title: "grub load error 18"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by urrohit on 2010-03-12
hi its rohit ..

i was getting **grub load error 18** some 5 months back .. then i called the serviceman & is corrected it somehow.. he told me that I had not installed it correctly .. thats why there was some problem with BIOS & also told that partitions are not corect...it was** ubuntu 9.04** **ultimate 2.3**

after some days i installed ubuntu 9.04 ultimate edition 2.3 . I forgot to give the swap area &the very next day i **grub load error 18**
i corrected it by removing the **CMOS battery** & the **JUMPER of motherboard**

in the first weak of february .. i installed **ubuntu 9.04** [B]ultimate 2.4 ..
[/B]now again i am getting  [B]grub load error 18 

please get me rid of this problem  ..:p
[/B]

---

### Post by tom4everitt on 2010-03-12
If I were you I would use ubuntu 9.10 instead. It features grub2 (instead of grub in 9.04) that automatically set itself up correctly (most of the times at least :) )

Here you can read about the grub errors, if you're interested: [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

---

### Post by urrohit on 2010-03-13
> **tom4everitt said:**
> If I were you I would use ubuntu 9.10 instead. It features grub2 (instead of grub in 9.04) that automatically set itself up correctly (most of the times at least :) )

Here you can read about the grub errors, if you're interested: [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)
thak you sir i will try ubuntu 9.10 I hope i will not get those errors anymore

---

### Post by coffeecat on 2010-03-13
> **urrohit said:**
> thak you sir i will try ubuntu 9.10 I hope i will not get those errors anymore

Before you install 9.10, it might be worth investigating why you get error 18 with legacy grub.

From the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html"):

> 
18 : Selected cylinder exceeds maximum supported by BIOS
This  error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).... which suggests a BIOS problem, which is likely to be just as problematic in whatever version of Ubuntu you choose. I notice that you say that there was some problem with the BIOS and that you temporarily solved this by resetting the CMOS.

You need to look at your hardware and BIOS. Is this an old machine? Because you shouldn't be getting this with recent machines. Even that text message in the grub error is pretty pre-historic. "...larger than 8GB in general..." :-s

---

### Post by louieb on 2010-03-13
> **coffeecat said:**
> .. From the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html"):... which suggests a BIOS problem...:-s

+1 to coffeecat's post

The workaround: before installing - use Gparted - create a small 200MB - 1GB partition at the start of the hdd and mount it as /boot - when done partitioning it should look something like this: 


[LIST]
[*]/boot (200MB - 1 GB)
[*]/ (root)  - (7GB - 15GB)
[*]/home - (whatever is left)
[*]swap  - (.5 to 1 GB - the more memory you have the smaller it can be).
[/LIST]

Then you will have to use manual partitioning - select each of the partitions and tell  the installer where to mount each partiton.

---

### Post by lkraemer on 2010-03-15
I'm wondering if you have a 3.5" floppy in your machine, as I am
having the same problem when I have the floppy enabled.  Right now
I have the floppy disabled, and I haven't seen the problem for a couple
of months.  I'm running Ubuntu 8.04.4 LTS and my Motherboard is an
EVGA 650i if memory serves me correctly.

EVGA Motherboard 650i

Motherboard 122-CK-NF66-T1 with 2 IDE (Master & Slave) Ports
and 4 SATA Ports. Only one Harddrive (Western Digital 500 Gig IDE
MASTER and one IDE DVDRW IDE SLAVE are connected to the Primary IDE Port)


It might be worth a try.

lk

---

