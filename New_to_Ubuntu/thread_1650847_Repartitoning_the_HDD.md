---
title: "Repartitoning the HDD"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by Brian_new_to_linux on 2010-12-22
Some weeks ago I installed 10.10 netbook remix on a Acer aspire one that had the Linpus Lite.  Being the cautious type I left 30Gb on the HDD for Linpus. As am more than happy with Ubuntu I would like to use  all of the HDD for it now. How do I do this?

Thanks in advance!

Beian

---

### Post by Hippytaff on 2010-12-22
if you type```
gksudo gparted
``` you should be presented with gparted from which you can extend, move, delete etc partitions
 
Edit -> I don't remember if gparted comes already installed, so you might have to install it, also you might have to do this via a live cd anyway because the partition your extending might need to be unmounted - [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by amjjawad on 2010-12-22
> **Brian_new_to_linux said:**
> Some weeks ago I installed 10.10 netbook remix on a Acer aspire one that had the Linpus Lite.  Being the cautious type I left 30Gb on the HDD for Linpus. As am more than happy with Ubuntu I would like to use  all of the HDD for it now. How do I do this?

Thanks in advance!

Beian

You need the LiveCD/USB for Ubuntu. Boot your machine from it and start GParted (System > Administration > GParted).

Take a screenshot and post it here. Don't quit the live session, I need to see your partitions to that I could offer a better advice.

---

### Post by amjjawad on 2010-12-22
> **Hippytaff said:**
> 
 
Edit -> I don't remember if gparted comes already installed

GParted is not installed by default starting form Ubuntu 10.04. One needs to install it ;)

However, the best is to boot up from the LiveCD/USB :)

---

### Post by Hippytaff on 2010-12-22
> **amjjawad said:**
> GParted is not installed by default starting form Ubuntu 10.04. One needs to install it ;)
 
However, the best is to boot up from the LiveCD/USB :)
 
Thought so, I buggered up my ubuntu messing around with gparted, had to do  fresh install so back-up is good advice too ;-)

---

### Post by amjjawad on 2010-12-22
> **Hippytaff said:**
> Thought so, I buggered up my ubuntu messing around with gparted, had to do  fresh install so back-up is good advice too ;-)

Ahhh, and I have to use the unallocated space on my 500GB HDD and add more OS's as the current ones feel lonely :P hehehe.

---

### Post by Hippytaff on 2010-12-22
I've given up dual/triple/multi booting for a while. Ressurecting old laptops now, so your probably better placed to give advice on this ;-)

---

### Post by amjjawad on 2010-12-22
> **Hippytaff said:**
> I've given up dual/triple/multi booting for a while. Ressurecting old laptops now, so your probably better placed to give advice on this ;-)

HOOHAA, you know where to discuss these stuff, buddy :D

I'm waiting for you there ;)

---

### Post by Brian_new_to_linux on 2010-12-22
Thanks for your help...but i solved this by deleting the partition in system and renaming and mounting it as "new volume" -I  now have 30Gb of private storage space for files. RESULT!
Brian

---

