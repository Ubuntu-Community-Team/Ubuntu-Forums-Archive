---
title: "some question about installing ubuntu on a new system"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by werty2010 on 2011-01-18
i'm thinking about installing ubuntu on my laptop
i checked out the download page and the name of the iso was: 'ubuntu-10.10-desktop-amd64.iso'

does amd refer to the amd processor?

mine is intel i3 and the graphic card is ati hd 5650
will i have any problems with performance or drivers?

also any tips i should consider?

if i use the alternative install,how can i find out my keyboard type through $indows before i proceed?

---

### Post by cariboo on 2011-01-18
The amd64 just denotes that it is a 64-bit version. It will work with any 64-bit cpu.

The AMD/ATI devs are a bit slow writing drivers for newer graphics chipsets, I'd suggest you try a Live CD before you decide to do an installation.

---

### Post by Quackers on 2011-01-18
I think amd were the first 64 bit processors (not sure) but anyway, I have Intel processors and the amd64 version is installed on my system with no problems.
Try the live system before installing it, to make sure that all h your hardware works ok. If there are any problems try 10.04, as that is a Long Term Support version (3 years) and has better hardware support.

---

### Post by erudite on 2011-01-18
That does refer to the AMD processor I believe however most processors now work with 64 bit download.

I would not advise the alternative install as it does not include a GUI.  If you look at all the different downloads you can also download 32 bit.

I am not sure if you will have any problems with performance regarding the video card however it should be easy enough to search and see if anyone else is.

Not sure about keyboard type...you can test with normal GUI install before you install....

---

### Post by cariboo on 2011-01-18
Intel came out with 64-bit processors first, but there instruction sets weren't backwards compatible, whereas AMD's version was from the start. There is an Intel 64-bit version available from Debian, but is is more aimed towards [itanium]("http://en.wikipedia.org/wiki/Itanium") cpus.

---

### Post by werty2010 on 2011-01-19
im one step before installation...

if i have installed ubuntu (using live cd) and for some reason i want to remove it completely from hdd, how can i do that?

---

### Post by 3rdalbum on 2011-01-19
> **werty2010 said:**
> im one step before installation...

if i have installed ubuntu (using live cd) and for some reason i want to remove it completely from hdd, how can i do that?

Ubuntu will create a couple of partitions for itself, so you would remove those partitions to create free space, then using a partitioning tool to up-size the Windows partition to fill the disk again. Then boot up your Windows CD, run the recovery console and run the "fixmbr" command. Reboot and everything will be back to normal.

CAUTION: Before doing any partitioning operations, make sure you're fully backed-up.

That's if you're dual-booting. If you're removing Windows to use Ubuntu, then just erase the hard disk and reinstall Windows.

---

### Post by werty2010 on 2011-01-19
> **3rdalbum said:**
> ...
Then boot up your Windows CD, run the recovery console and run the "fixmbr" command. Reboot and everything will be back to normal.
...



in my case i dont have a windows cd (laptop's company new policy) 
is there some other way of doing that?

---

### Post by sandyd on 2011-01-19
> **werty2010 said:**
> in my case i dont have a windows cd (laptop's company new policy) 
is there some other way of doing that?
You create one from windows
But if you have to...
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

