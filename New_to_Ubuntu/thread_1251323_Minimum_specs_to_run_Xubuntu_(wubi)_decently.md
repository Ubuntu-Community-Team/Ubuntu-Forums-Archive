---
title: "Minimum specs to run Xubuntu (wubi) decently?"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by SydneyGB on 2009-08-27
I was under the impression that Xubuntu would run on a 256M memory machine in 5 GB HD space.  This seems to be true, as I'm typing to you on just such an install.  :)  But after the first week or so, Xubuntu seems to run rather sluggishly at times.  I installed it using Wubi (see notes about partitioning fear below :).

The machine has a 10GB hard drive, with Windows 98 living on the other half of the drive.  I have a number of old machines on which I'm experimenting with Linux.  I have a P75-100 running DSL on 800MB of HD space (only recently realised DSL is meant as a recovery platform... heh).  As a pack rat who hates to throw anything out, I'm trying to breathe new life into these old beasts.

The Windows 98 portion runs with decent speed. Basically I only need that for games and my scanner (setting up my parport scanner in Xubuntu is a mountain I am still preparing to climb).  But I'm getting more and more lag in Xubuntu lately.  Right now I'm running Firefox with three open tabs, terminal, and an instance of the file manager, and my CPU meter keeps bobbing up and down, from about 15% usage up to 45% or so as I type.  I have minimal packages installed, and I'm keeping a log of what I've installed.

I realise that the Wubi install is slightly slower than a true install would be, but I'm terrified of partitioning my drive (I backed up my most precious files from the Windows system at least three times on my primary machine before I realised I could install with Wubi).  I'm also searching and experimenting with other Linux distros via VirtualBox to find one that will run happily in the space and memory it would have on this box.

The system's relevant specs are:
Dell Optiplex GX1p
10GB HD (currently half Win98 half Xubuntu) + 1GB HD used mostly as a Windows swap file
256MB memory

I could use some advice on optimisation of Xubuntu or on a more suitable Linux distro that I can use to do basic internet surfing, writing, email, etc.

---

### Post by inobe on 2009-08-27
wubi is just a taste and no way near the actual hard drive install.

example: i acquired an old dell inspiron 1200 with built in 256mb memory' some of that allocated to onboard intel 915gm video, and installed kubuntu via wubi.

it dragged badly.

tried ubuntu.

was a little faster untill apt-update started.

couldn't run firefox and apt at the same time.

might as well wait for apt to finish, this was the case.

got fed up and thought virtual disks/ loopback systems are slow !


popped in the ubuntu disk a destroyed windows xp partition..... selected guided.


currently ubuntu 9.04 is installed by itself and only notice slow downs when multi tasking, multiple browsers and terminals, apt, setting up samba shares via terminal and wile chatting on pidgin, desktop affects working etc....

i am very pleased and could only imagine how much more faster xubuntu would be.

---

### Post by inobe on 2009-08-27
system specs

# Intel Celeron M 350 (1.3GHz/1MB)
# 256MB PC2100 DDR
# 40GB 4,200rpm Hard Drive
# 24x CD-RW/DVD Combo Drive
# 15" XGA LCD and Intel Extreme 2 Graphics with 64MB Shared Memory
# AC'97 Audio
# v.92 56Kbps Modem and 10/100 Ethernet
# Three USB 2.0 and One Type II PC Card
# 13" x 10.6" x 1.5" @ 6.6 lbs.

[http://ubuntuforums.org/attachment.php?attachmentid=126133&d=1251165736](http://ubuntuforums.org/attachment.php?attachmentid=126133&d=1251165736)

---

### Post by Dark Aspect on 2009-08-27
> **SydneyGB said:**
> 
The system's relevant specs are:
Dell Optiplex GX1p
10GB HD (currently half Win98 half Xubuntu) + 1GB HD used mostly as a Windows swap file
256MB memory


[Puppy Linux]("http://www.puppylinux.org/") runs ok on my 550 Mhz. Wikipedia says that model of Optiplex has a core between 400-600 Mhz, so might be worth looking at.

---

### Post by snowpine on 2009-08-27
Hi Sydney, your problem is that your computer is pretty much the bare minimum to run Xubuntu, and then you're using Wubi, which is an extra layer on top of that. Don't be scared of partitioning; the installer will do it automatically for you if you select the option to resize the windows partition and install in the free space. Good luck!

---

### Post by gn2 on 2009-08-27
I would suggest giving [Antix]("http://antix.mepis.org/index.php/Main_Page") a try.

---

### Post by Dark Aspect on 2009-08-27
> **gn2 said:**
> I would suggest giving [Antix]("http://antix.mepis.org/index.php/Main_Page") a try.

Hm..

[QUOTE=link]antiX-M7-M8 will not run (yet) on older processors such as Pentium I (it seems that PII is ok, but PII MMX may not boot), AMD K5, and AMD K6 as it uses an up to date i686 kernel. antiX-Spartacus should.[/QUOTE]

[QUOTE=Wikipedia]GX1p, Intel 440BX AGPSet, **Pentium II** 400, 450 or Pentium III 450-600, 100 MHz SDRAM,[/QUOTE]

How do you know if that model has mmx?

---

### Post by gn2 on 2009-08-27
Pentium II are all MMX.

[http://en.wikipedia.org/wiki/Intel_Pentium_II](http://en.wikipedia.org/wiki/Intel_Pentium_II)

And I would still suggest trying it.

---

### Post by Dark Aspect on 2009-08-27
> **gn2 said:**
> Pentium II are all MMX.

[http://en.wikipedia.org/wiki/Intel_Pentium_II](http://en.wikipedia.org/wiki/Intel_Pentium_II)

Cool I am idiot,

Unrelated, I might try antix on one of my older computers. Puppy Linux with its newer versions are beginning to run slow on > 400Mhz.

---

### Post by bodhi.zazen on 2009-08-27
Unforutnately Xubuntu is not *that* light.

On older hardware I suggest Slackware and variants - Slax, Zenwalk, Wolvix.

Slax runs KDE on 99 mb of RAM.

all of these will give you better performance and more features then a light weight disto.

Of the lightweights, currently I like Slitaz. Puppy and DSL are also options. The problem with the lightweights, limited repositories and you may not like the interface.

See also : [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

