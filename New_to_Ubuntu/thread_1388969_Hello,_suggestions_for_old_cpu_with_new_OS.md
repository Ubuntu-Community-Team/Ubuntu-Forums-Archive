---
title: "Hello, suggestions for old cpu with new OS"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Dunwoodyhum on 2010-01-23
I have an p3 with 256 MB ram that I have tried to install Ubuntu on.  Mostly to learn and play.  I am reading Keir's pocket guide but honestly it has been more fun to play with the computer that actually read the instructions.  So I have some studying to do, still.

The system was slow, as you might imagine so I dropped to Xubuntu using some command that I found here.

This speed is better but still slow and there are periods of lethargy.  I suppose some more RAM is in order but I'm not ready to spend money on it at this point.

Finally the questions...Would I be better off starting over with a fresh install of Xubuntu?  Which release?  Does having the dual boot cause further problems?  (I could wipe out win98 completely.) 

Regards,

Chris

---

### Post by FreezWay on 2010-01-23
go system>admin>system monitor

how much swap are you using?

---

### Post by halitech on 2010-01-23
Instead of doing a fresh install of Ubuntu or Xubuntu, I would suggest doing a minimal install (takes you to a command line install) and then add LXDE. Its a much lighter Desktop Environment and may/should run better. Xubuntu used to be a very light distro but the last few versions haven't been much lighter then plain Ubuntu.

---

### Post by Revolutionary101 on 2010-01-23
I suggest using a new clean install of Xubuntu 9.10 or you could wait until Lubuntu 10.04 comes out in April.

Lubuntu is supposed to be a new official version of Ubuntu that uses the LXDE desktop enviroment. From what I have heard it is supposed to be faster than Xubuntu.

To see how Lubuntu would work on your computer type this into terminal.

```
sudo apt-get install lubuntu-desktop
```

---

### Post by Dunwoodyhum on 2010-01-23
I have opened the system monitor.  Please explain "swap"?

I like the suggestion of using LXDE and I will try the Lubuntu an report back.

Thanks all

---

### Post by FreezWay on 2010-01-23
under the "resourses" tab its on the second graph. its the green line. swapping is when your computer starts using your (slow compared to ram) hard drive as ram b/c it doesn't have enough ram.

---

### Post by Dunwoodyhum on 2010-01-23
Swap is 2.7%.  Seems lower than expected?

Lubuntu install attempt tells me that

The following packages have unmet dependencies:
   Lubuntu-desktop: Depends: wicd but it is not going to be installed

unquote

Does not sound promising.  Is it possible to do a fresh install of Lubuntu?

---

### Post by egalvan on 2010-01-23
256M is low for "modern" systems.
As *halitech* reommended, LXDE may provide a workable GUI for you.

If not, try Puppy Linux, or Slitaz.

Both are designed to run on low resources, especially low RAM (less than 512m :) )

Puppy runs fully in RAM  with 256M, and is FAST. It can also be installed to hard drive.
[http://www.puppylinux.com/](http://www.puppylinux.com/)


slitaz is similarly designed for low resource.
It had a good write-up in DistroWatch recently (maybe two weeks ago)
[http://distrowatch.com/weekly.php?issue=20100111](http://distrowatch.com/weekly.php?issue=20100111)


then there is TinyMe Linux
[http://tinymelinux.com/forum/index.php](http://tinymelinux.com/forum/index.php)

and Tiny Core Linux
[http://tinycorelinux.com/](http://tinycorelinux.com/)

All of these are small downloads

Puppy approx 110M
Tiny Core approx 10M  (yes TEN MegaBytes )

(they're small, try them all :) )


Then you have this article (a bit dated, though... DSL has fallen behind in updates, for istance)
[http://www.informationweek.com/news/software/linux/showArticle.jhtml?articleID=203100989](http://www.informationweek.com/news/software/linux/showArticle.jhtml?articleID=203100989)

---

### Post by Settwi on 2010-01-23
If you really want [X]ubuntu,  then you should just do a clean install from a CD.  wipe out win 98, or, IF you just want linux, have you tried puppy linux?  It's very lightweight, and easy to install, from my experience.
here's a download link!
[Click me!](http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.2retro-k2.6.21.7-seamonkey.iso)
THIS WILL DOWNLOAD THE .ISO FILE WHICH yOU CAN BURN WITH [THIS](http://www.terabyteunlimited.com/downloads/burncdcc.zip)
(make sure you're in windows 98 when u burn)

---

### Post by jmszr on 2010-01-23
Dunwoodyhum,

Here is a link for the Masonux torrent:[http://linuxtracker.org/index.php?page=torrent-details&id=69378f8b0487a83261dfca9f5ddb8815b88c7964](http://linuxtracker.org/index.php?page=torrent-details&id=69378f8b0487a83261dfca9f5ddb8815b88c7964) .

This release is based on Ubuntu 9.04 so it is pretty stable.
Here is a description of Masonux:

	Masonux is derivative of Ubuntu Linux using the LXDE desktop environment created using remastersys.
Masonux contains the following: Ubuntu 9.04 base/command-line install, LXDE, Firefox, Pidgin, Synaptic Package Manager, ubiquity graphical installer, and remastersys.
Installation requires 256MB of RAM, 2GB of hard drive space. The base install will use about 1GB of hard drive space and 60MB of RAM at boot.
[http://sites.google.com/site/masonux/home](http://sites.google.com/site/masonux/home)

Perhaps that will work for you.

---

### Post by Dunwoodyhum on 2010-01-23
Looks like I will try Puppy Linux.   The release notes are a little over my head but if it doesn't work out I will do a fresh install of Xubuntu or Lubuntu when it becomes available.

Thanks for your help.

---

### Post by knurledflanges on 2010-01-23
Definitely give Puppy a try... it is super fast even on older machines. As opposed to so much else out there, it really gives the feeling that the designers were "on your side" in trying to get dignified everyday performance out of an older system.

---

### Post by teresaejunior on 2010-01-23
antiX should be lighter than Xubuntu, and it's like Ubuntu (Debian based) really grateful to it! Never tried puppy. Boots using about 30MB of ram and has powerful and modern apps. 2 apps that do same thing for you to choose. Small LiveHD size.

---

