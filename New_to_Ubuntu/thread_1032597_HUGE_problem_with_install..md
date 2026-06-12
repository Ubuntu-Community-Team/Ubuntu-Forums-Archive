---
title: "HUGE problem with install."
date: 2009-01-06
forum: New to Ubuntu
---

### Post by MaximoMilkman on 2009-01-06
So as we speak i am on my laptop looking at my desktop trying to install Xubuntu i want to dual boot it with windows xp BUT it wont allow me to make a partition for it and windows.. i select GUIDED partition and it only gives the option to overwrite my whole partition and have 100% xubuntu it wont let me like use the slider and tell it to share with windows.. its weird i need some help when i ran the partion editor it says i have a /dev/sda5 linux-swap which is 721 MBs along with /dev/sda2 extended also 721 MBs does this have to something to do with it.?? if you need more info out of me just ask.. 


***THIS IS NOT MY SCREEN SHOT*** BUT this is the part im talking about my window has no slider to share it just has 100% ubuntu 

[http://www.herman.linuxmaniac.net/p24/013.png]("http://www.herman.linuxmaniac.net/p24/013.png")



This is what mine says

How do you want to partition the disk?

Before /dev/sdb 100%

after Ubuntu 8.10 100% ***Note it says Ubuntu 8.10 when i want Xubuntu and the disc and everything says Xubuntu***

HERE ARE MY OPTIONS

Guided - Use entire disk
SCSI# (0,0,0) (sdb) - 129.0 MB SMART G2 DELL MEMORY KEY

Manual ** EVEN WHEN I HIT MANUAL IT STILL SAYS 100% MANUAL

---

### Post by avtolle on 2009-01-06
First of all, defrag the drive (if you've not done so) more than once. Second, resize the XP partition to create some space. Third, the existence of the swap partition may be playing a part in this as well. 

BTW, how many partitions do you have on the HDD at present?

---

### Post by LowSky on 2009-01-06
maybe you should try running disk defragment from windows first, then run the partition editor from the LiveCD

---

### Post by MaximoMilkman on 2009-01-06
How do i resize the XP partition?? i know how to defrag my drive but not how to make space please tell! Thanks a bunch for helping me out! By the way i think since i had a USB flash drive in that affected something im defraging the HD right now though

---

### Post by avtolle on 2009-01-06
OK, you are using a live CD to do this, correct? If so, then once into the partitioner, you should select the xp partition, and tell the partitioner to resize it. I don't recall you posting the size of your HDD; I'd give the Xubuntu install (root parition) at least 10 GB, if you aren't going to have a separate /home parition. 

If you aren't using a live CD to partition, the HDD is mounted, and you shouldn't try to do anything with partitions, etc., on a mounted drive.

---

### Post by avtolle on 2009-01-06
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) may be of some help to you, too.

---

### Post by avtolle on 2009-01-06
[http://psychocats.net/ubuntu/dualboot#partitioning](http://psychocats.net/ubuntu/dualboot#partitioning) is a better link for you to look at.

---

### Post by MaximoMilkman on 2009-01-06
I have 69 gigs free i just installed windows over again this morning *Since i previously told xubuntu to overwrite my WHOLE HD i just defragged my HD also.. I want to dedicate about 20GB to Xbuntu and 40 for windows.. how can i do this???

---

### Post by theozzlives on 2009-01-06
How much do you have free? you want 10 GN for /, the amt of RAM for swap, and the rest for /home

---

### Post by theozzlives on 2009-01-06
How much do you have free? you want 10 GB for /, the amt of RAM for swap, and the rest for /home

---

### Post by MaximoMilkman on 2009-01-06
im sorry ozzvilves i dont understand what you mean.. but i would like about 30gb for xubuntu and 39gb for windows xp how can i do this.. im guessing i have to do this from the LIVE CD or whatever.. . previously this option was non existent but i will try again..

---

### Post by avtolle on 2009-01-06
You are booting Xubuntu from the live cd, correct? I presumed you had earlier, given your first post. Again, take a look at the second link I posted.

---

### Post by MaximoMilkman on 2009-01-06
Previously they didnt give me an option to use a slider or resize to make space for windows.. idk why im going to check and see if it will let me now that i defraged my HD

---

### Post by MaximoMilkman on 2009-01-06
alright now it gave me the slider option hopefully all goes well i designated about 40 percent to xubuntu and 60 to xp im getting excited!!! linux is a very hard operating system for me to learn by any chance does anyone know of any beginner tutorials to follow that are helpful.. i want to figure out how to install new XFCE themes.. and how to install Adobe flash also wasup with these reposotories things.. how do those work .. and how do you open it up for multireverse or something like that..??

---

