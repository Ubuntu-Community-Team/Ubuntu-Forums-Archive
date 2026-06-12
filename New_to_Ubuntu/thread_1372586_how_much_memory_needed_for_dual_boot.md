---
title: "how much memory needed for dual boot?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by jocelynbennicoff on 2010-01-04
I'm looking for a new laptop and I want to have both Windows 7 and Ubuntu on it.  I'm looking at some laptops with 4 GB RAM and 500 GB HDD.  Is this enough memory to have both OS's on there?

---

### Post by cenzorrll on 2010-01-04
lucky for you the amount of RAM is completely independent of the number of operating systems.  The RAM is used for all your processes and programs that need quick access to the processor.  That means, your running operating system, antivirus, pretty much everything you would see in your taskmanager (windows) or system monitor (ubuntu).

what does matter is your hard drive space.  windows 7 at minimum requires 15gb and ubuntu usually can fit in a 3gb space.  however, this leaves little room for anything else.  so, your 500 gb hard drive will have no problem with this.

when partitioning i would have a shared partition between windows 7 and linux, that way you can keep your music etc, in one place.  which also means you can leave your ubuntu partition pretty small and let windows do it's bloat thing. (i don't think i've ever used more than 7gb with a linux system, not counting music and such)

---

### Post by Max_Mackie on 2010-01-04
If you're dual booting, RAM shouldn't matter (you're either running one or the other so theres no sharing). However, Windows (since Vista) needs 1GB of RAM just to run Aero -- so you'll be looking at MINIMUM 2GB for a smooth run. 

As for hard drive space, I believe the Ubuntu install takes ~10GB and Windows might take a little more. The question here is how much data youll be storing on it (lots of music/movies).

First things first though. Make sure you install Windows first and set up drive partitions with Ubuntu. I would make:

1- Windows Partition (~20GB)
2- Ubuntu Partition (~15GB)
3- SWAP (for linux, very small)
4- Media (the rest of the HDD)

---

### Post by J V on 2010-01-04
Better idea...

1- Windows Partition (~30GB)
2- Windows user partition (Rest)
3- Ubuntu Partition (~15GB)
4- Ubuntu /home Partition *with symlinks to #2, this will let you share* (1gb +-)
5- SWAP should be double ram but youve got plenty, probably not neccesary

Sadly, theres no encrytion with this... but you get to share between windows and ubuntu...

Anyway, you will fall in love with ubuntu in no time :)

Of course giving the operating systems and your /home a bit more room to breathe is a good idea...

rather than stick everything on a windows partition (ugh) make a few logicals and for windows and linux... (You've one serious HD there lol)

---

### Post by Max_Mackie on 2010-01-04
> **J V said:**
> Better idea...

1- Windows Partition (~30GB)
2- Windows user partition (Rest)
3- Ubuntu Partition (~15GB)
4- Ubuntu /home Partition *with symlinks to #2, this will let you share* (1gb +-)
5- SWAP should be double ram but youve got plenty, probably not neccesary

Sadly, theres no encrytion with this... but you get to share between windows and ubuntu...

Anyway, you will fall in love with ubuntu in no time :)

Ahh I forgot about symlinks! I'm going to set that up on MY box. Thanks J V

---

### Post by J V on 2010-01-04
You're welcome :)

---

### Post by chuina on 2010-01-04
enough :P

---

### Post by gabo.cr on 2010-01-04
RAM is important only if you are using VirtualBox.
Like running Win inside Ubuntu at the same time.
For Dual booting is not a problem at all.

---

### Post by jocelynbennicoff on 2010-01-05
Thanks for the replies!  Could someone please explain what a partition is, how to set it up, etc?

---

### Post by Max_Mackie on 2010-01-05
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by audiomick on 2010-01-05
Regarding your swap space.
JV suggested swap = 2x RAM.
This is not necessary with 4GB RAM. That is an adage from the times when RAM was typically 256MB or so.

There is a consideration if you want hibernation to work. In that case, your swap partition needs to be a fraction bigger than your RAM, as the hibernate function writes the contents of RAM into the swap space. If that is not an issue for you, you should be right with 1GB or so. I have 4GB in mine, and practically never get into using the swap.

---

### Post by egalvan on 2010-01-05
You can also place XP´s ¨My Documents¨ folder in the shared partition, and really shrink the XP OS partition.

Here is a decent how-to on moving MyDocs

[http://www.thundercloud.net/information-avenue/my-documents/](http://www.thundercloud.net/information-avenue/my-documents/)

many others available via google.

:)

BTW, this is a great help if you need to restore/re-install XP...
it´s similar to a seperate /home under Linux...
all your data is belong to you :)

---

### Post by bodhi.zazen on 2010-01-05
> **jocelynbennicoff said:**
> Thanks for the replies!  Could someone please explain what a partition is, how to set it up, etc?

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

