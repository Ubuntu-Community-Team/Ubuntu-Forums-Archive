---
title: "A Complete switch"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by Zirts on 2010-06-27
Hi,

I have now tested out Ubuntu and I love it.

Now what I'm planning to do is to completly clear my disc meaning that I get rid of everything on it including Windows, and then installing Ubuntu from the CD I'm making atm.

Now my questions are: 

1. Are there going to be any driver problems when I get rid of Windows with it's files?

2. How do I get rid of Windows completely so that my disc is cleared from all that trash?

---

### Post by sailor2001 on 2010-06-27
The install cd gives you a choice on how you want to install ubuntu... Windows is needed for some games, such as war craft. I don't play games so haven't used windows for a very long time..I do like windows to manage my hard drive partitions.so I keep it. (dual boot)

---

### Post by nhasian on 2010-06-27
I'm all for blowing away windows but if your hard disk has a system restore partition from the factory i would recommend hanging on to that.  In the future if you decide you need windows again or even if you want to resell your computer down the line you can use it to restore windows.

during the Ubuntu installation always choose Manual partitioning option so you can specify the partitions.  you can delete the larger NTFS partition which contains windows, but keep the smaller partition which is most likely your factory restore partition.  then you can create 3 more partitions:

/ (root) as EXT4 12 gigs is probably plenty
SWAP partition the same size as the amount of ram in your system
/home partition also EXT4 should be the remainder of your drive as thats where all your personal data and media will be.

---

### Post by cascade9 on 2010-06-27
> **Zirts said:**
> Hi,

I have now tested out Ubuntu and I love it.

Now what I'm planning to do is to completly clear my disc meaning that I get rid of everything on it including Windows, and then installing Ubuntu from the CD I'm making atm.

Now my questions are: 

1. Are there going to be any driver problems when I get rid of Windows with it's files?

2. How do I get rid of Windows completely so that my disc is cleared from all that trash?

1- if you are running ubuntu with no problems now, then removing windows wont make any differernce to the drivers (windows uses totally different drivers than linux....well, apart from some dodgy wireless networking cards that use the windows drivers with ndiswrapper). 

2- when you go to install ubuntu, choose 'manual partitioning' and then delete all the old partitions. Easy. 

> **sailor2001 said:**
> The install cd gives you a choice on how you want to install ubuntu... Windows is needed for some games, such as war craft. I don't play games so haven't used windows for a very long time..I do like windows to manage my hard drive partitions.so I keep it. (dual boot)

Ummm....warcraft? Apart from the original 'warcraft-orcs and humans' all the warcraft games work under WINE.  Even WoW, which according to some sources, runs better with WINE than it does on windows. :)

---

### Post by Zirts on 2010-06-27
Thanks for all the answers!!

I have 1 more question though, now that my .ISO is downloading, I saw that the size of that .ISO is 699,4MB, so am I really downloading the right thing?  Name of it is Ubuntu-10.04-desktop-i386.iso

I wonder about this becouse when I downloaded Wubi, I remember it was a lot bigger...

---

### Post by cascade9 on 2010-06-27
Ubuntu-10.04-desktop-i386.iso is the right one (unless you wanted 64bit, or a different desktop enviroment). 

I have no idea about WUBI, I've never used it.  ;)

---

### Post by da burger on 2010-06-27
That's the right name and about the right size (it's made to fit on a cd).

---

### Post by nhasian on 2010-06-27
can your CPU handle 64bit instructions?  you probably want ubuntu 64bit 

> **Zirts said:**
> so am I really downloading the right thing?  Name of it is Ubuntu-10.04-desktop-i386.iso

---

### Post by slooksterpsv on 2010-06-27
Way to go.

The suggestions they gave above will absolutely work.

If you're not sure if the drivers are there for your computer, boot off the live cd or install wubi and make sure first.

---

