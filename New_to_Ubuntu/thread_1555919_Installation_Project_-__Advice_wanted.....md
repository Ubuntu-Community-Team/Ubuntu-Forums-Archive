---
title: "Installation Project -  Advice wanted...."
date: 2010-08-18
forum: New to Ubuntu
---

### Post by GaryTheCat on 2010-08-18
My ex has an old PC - spec to follow:

What she wants is a machine to browse the web but ultimately our 6 year  old son to use so he can also browse the web and make use of educational  software: The question is, which variant would be best to install and  whether a different front end might be appropriate.

The Specs......

Processor: AMD Athalon 64 3400+ @ 2.19 GHz
RAM: 384MB (seems low but that's what's there)
Display adapter: ATI Radeon Xpress 200 Series
HDD: 1 disk partitioned 3 ways:

Backup - 7.31 GB FAT
C:\ 29.99 GB NTFS 16.4 GB Free
D:\ (Data) 111.24 GB NTFS 51.5 GB Free

My plan is to shrink D:\ and make a new partition to put the chosen OS  in and then mount the D:\ drive in fstab so that what's currently on  there can be shared between the 2 OSs.

My questions are:

1.  Which OS would sit best on this machine?
2.  I know there are normally gains to be made in adding more memory - but can I avoid it?
3.  Will the live CD of which ever OS it is allow me to choose the new partition?
4.  Any recommendations for cool educational games for a 6 year old to play?

I think that's about it :wink:

TIA

Gary

---

### Post by Locke_99GS on 2010-08-18
My 5 year old daughter's computer is lesser spec'd in every way. She uses Ubuntu Lucid as the sole OS without issue.

The LiveCD installer would be able to handle the partitioning duties, though I usually find myself prepping ahead of time with gparted.

My daughter usually plays the flash games on disney.go.com, pbskids.org, and nickjr.com. There are a few games and tools we've installed from the repos that she also enjoys. One is a potato character game of some sort, one is a tool for creating vector caricatures. She likes messing around with it. She also listens to Hanna Montana music streamed from (i think) playlist.com.

---

### Post by GaryTheCat on 2010-08-18
Thanks for that - the HM noises sound like an interesting scripting project lol

---

### Post by GaryTheCat on 2010-08-18
Another Q....

Is it worth installing the 64 bit version considering how little RAM this machine has?

---

### Post by GaryTheCat on 2010-08-19
Bump

---

### Post by GaryTheCat on 2010-08-19
Bump bump

---

### Post by Locke_99GS on 2010-08-20
I am running 64bit on all the computers that are able to. My daughter's old PC is 32bit only, though, so she runs this.

When I switched from 32bit to 64bit OS circa Intrepid or Jaunty, my unmetered eye detected a bit more snappiness in overall use, such as menus opening, the kernel booting, those sorts. I know others have said that 64bit aplications consume more RAM, but I haven't noticed this. Without direct comparison, it appears that I consume roughly the same amount of RAM as I have in the past, given room for the bit more software bloat I currently enjoy.

If somebody has links to credible and objective comparisons of RAM usage between identical installs a 32bit Linux OS and a 64bit Linux OS, such as from Phoronix, that'd be welcomed.

IMO, if the machine is capable of 64bit, I'd use it. If you're concerned about the amount of available RAM, consider something of the sort of LXDE as a DE rather than GNOME or KDE. It is far lighter, yet still simple enough a child could use it.

---

