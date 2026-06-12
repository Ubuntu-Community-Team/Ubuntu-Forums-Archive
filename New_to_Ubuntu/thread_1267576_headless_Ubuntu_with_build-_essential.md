---
title: "headless Ubuntu with build- essential"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by Windy Peaks on 2009-09-15
Ladies and Gentlemen of the forum:

Everytime I open My current laptop to work with the command line or C programming stuff My two beautiful children crowd Me on either side so I can show them some internet related cartoon or linux game.

I may have the problem beat, I got my hands on a very old toshiba satelite 220cds laptop (1996 I think?) that has very limited abilities. So now the won't ask Me for things it can't do.

Now I need to find a verion of Ubuntu (9.04 or older)that has only the command line and "build-essential" installed so I can do C programming.
The laptop has 32Mb of RAM and a hard drive with 1.25Gb on it so it's got to be a very small operating system.

Any thoughts ??

Thank You in advance.

Windy

---

### Post by ainsworth_t on 2009-09-15
Seeing as Ubuntu has the following system requirements as taken from the Ubuntu Community Documentation, it's probably not feasable to install Ubuntu on your laptop. 
> 
**Bare Minimum requirements**
It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the Alternate install CD to attempt such an installation. 
[LIST]
[*]300 MHz x86 processor 
[*]64 MB of system memory (RAM) 
[*]At least 4 GB of disk space (for full installation and swap space) 
[*]VGA graphics card capable of 640x480 resolution 
[*]CD-ROM drive or network card
[/LIST] 
However, a distro such as Damn Small Linux ([http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)) or Tiny Core Linux ([http://tinycorelinux.com/](http://tinycorelinux.com/)) might be more suitable. Damn Small Linux is a live CD that can be installed as a full Debian system which you can then install the build-essential package on. I'm not as familiar with Tiny Core but it has similar minimum requirements.

---

### Post by Windy Peaks on 2009-09-16
Great call, I did some mental googling and remembered  DSL 4.4, it's in last August's local computer magazine. 

You are correct once Your workout deleting the old windows partition and format it using fdisk choosing option 83 (normal linux) DSL loaded nicely.
I just need to double check the build-essential side of it so I can program in #C.

I don't have internet acess on that computer but I might think of something using the single USB port.

Thanks again for Your help

Windy









> **ainsworth_t said:**
> Seeing as Ubuntu has the following system requirements as taken from the Ubuntu Community Documentation, it's probably not feasable to install Ubuntu on your laptop. 

However, a distro such as Damn Small Linux ([http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)) or Tiny Core Linux ([http://tinycorelinux.com/](http://tinycorelinux.com/)) might be more suitable. Damn Small Linux is a live CD that can be installed as a full Debian system which you can then install the build-essential package on. I'm not as familiar with Tiny Core but it has similar minimum requirements.

---

