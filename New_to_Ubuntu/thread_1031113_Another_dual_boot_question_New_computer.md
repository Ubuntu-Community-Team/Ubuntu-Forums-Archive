---
title: "Another dual boot question: New computer"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by hiloguy on 2009-01-05
This has no doubt been addressed here but I can't find what I'm looking for, so here goes:  I'm about to order a new Dell XPS 1530.  What will be the best procedure for wiping Vista and installing Ubuntu 8.04 and XP-Pro as a dual-boot setup?  I have both CDs and will be using Ubuntu for everything except the few instances when I need WP.  I've heard several different "best" ways to do this, but I REALLY want this to work right, what with a new computer and all . . .

Thanks for any help here . . .:D

---

### Post by nhasian on 2009-01-05
parition your drives however you like and install Windows XP First.  then install ubuntu.  dont forget to get dell to refund you for your unused license of windows vista.

---

### Post by blazemore on 2009-01-05
They probably won't...

---

### Post by Michael.Godawski on 2009-01-05
hi, 

on this page I have posted a link to a great dual boot site.
Basically you should install Ubuntu **after** Windows:


[LIST]
[*][http://godawski.oxyhost.com/switch.html](http://godawski.oxyhost.com/switch.html)
[/LIST]

---

### Post by carml on 2009-01-05
If you try to install Ubuntu first,then when you install Windows it will not recognize Ubuntu,I say this because I had to reinstall Windows on a dual boot PC. :P

---

### Post by theozzlives on 2009-01-05
1. In your CMOS Setup, turn off your SATA capabilities and go with ATA (XP don't support SATA)
2. In your XP setup, delete your partitions and create your XP partition (say 1/2 the drive)
3. Install Ubuntu and choose manual partitioning.
4. Create a root (/) of say 10  GB.
5. Create a swap equal to your RAM.
6. Use the rest for /home.
7. Continue with the install.

---

### Post by Lisa Y on 2009-01-05
Agreed!

Install the windows partition FIRST...then install the ubuntu partition

---

### Post by hiloguy on 2009-01-05
Mahalo Plenny (That's Thank You in Hawaii!) for all the quick replies and even answers to my questions!  This Forum has been (and still is) an amazing resource.  Even better than Windoze Tech Support! :rolleyes:

I've been using Ubuntu on my laptop for nearly a year now and I love it.  I'm replacing my aging laptop and my 6-yr-old desktop with a new laptop and still need to use XP once in a great while, hence the dual boot thing.

Thanks again, everybody!  No doubt, I'll be back soon.:D

---

