---
title: "run windows programs"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by computerguts on 2010-03-13
how do you run any windows program that is windows based in linux?

---

### Post by tejashs on 2010-03-13
use "wine" application from synaptech packet manager
you might be able to run some of the applications 
although i think all windows applications have a counterpart for linux which you can try

---

### Post by oldsoundguy on 2010-03-13
You can't just out of the box.

Linux is NOT Windows. 

You can:
Install windows on a separate partition or
Install a Virtual Machine and install Windows into it or
Install Wine and run some (not all by any means) Windows programs IN Wine or

You can do as many have done and found alternative programs to the Windows programs in the Linux repositories and run them (Open Office, Gimp, and many others.

---

### Post by computerguts on 2010-03-13
thanks

---

### Post by NightwishFan on 2010-03-13
Knowing it is hard for beginners, I will tell you that the short answer is, you don't. At least do not expect or rely on them to work. Search for Linux based alternatives first. Only in a few cases is Windows software lock in even relevant. Gnu/Linux is not Windows.

At any rate, there are 2 viable simple alternatives. You can install Wine, and let your program execute natively on your GNU/Linux system. I would recommend this, as it is the most simple way and offers the best performance. First check the rating of your program here, if it is silver or above, then install the wine package by clicking below. Wine works just like Windows, just double click the .exe. If it does not work, right click the file and go to properties, and set the Wine program loader as the default program to open it.
[Click Here To Install Wine]("apt://wine")
[Search For How My Program Works]("http://appdb.winehq.org/")
[Ubuntu Wine Info]("https://help.ubuntu.com/community/Wine")

The second option is to install Windows in Virtualbox. This can offer better compatibility, but you are still require a legal Windows CD. This is also slightly more complicated. If your program works in Wine you do not need this method.
[Ubuntu Virtualbox Info]("https://help.ubuntu.com/community/VirtualBox")

Good luck, and please feel free to ask any questions. Just remember to try Linux applications first. I have found many much more satisfactory free software programs than I did proprietary ones.

---

### Post by ubu newb on 2010-03-14
With virtual box, is it possible to see your existing windows 7 partition and use it or do you have to install it's own partition?

---

### Post by cusinmex on 2010-03-14
Not all windows programs run normal on wine,
some will run slow, or you'll eventually run into
some issues.


Virtualbox just works like an application
it just opens up a window with the OS running inside
of it.

---

### Post by Paqman on 2010-03-14
> **ubu newb said:**
> With virtual box, is it possible to see your existing windows 7 partition and use it or do you have to install it's own partition?

A virtual machine is essentially a whole separate computer. You typically create the virtual machine then install the OS into it. Note that this means you have to have a second Windows license if you already have a copy of Windows installed the conventional way. 

AFAIK it's technically possible to import a pre-installed system into a virtual environment, but from what i've seen it's not easy.

---

### Post by The Pilgrim on 2010-03-15
> **Paqman said:**
> 
AFAIK it's technically possible to import a pre-installed system into a virtual environment, but from what i've seen it's not easy.

But is it possible to run a pre-installed XP from an external USB drive? And even if the bios cannot boot from USB port? 

Hope I'm not OT.

---

### Post by computerguts on 2010-03-15
Nightwishfan 

What do you mean by, let your program execute natively on your GNU/Linux system?

---

### Post by NightwishFan on 2010-03-15
Wine does not virtualize it, it just replaces Windows system calls with Linux ones, thus it runs natively as if it were a Linux program.

---

### Post by cerealtx on 2010-03-15
and as far as using a exsisting OS install, you would have to create a image of your harddrive for virtualbox more hassle than i believe its worth but thats me

---

### Post by QIII on 2010-03-15
While you won't really need to understand all of this, you might give the following a read:
 
 [http://en.wikipedia.org/wiki/Loop_device](http://en.wikipedia.org/wiki/Loop_device)
 
 WINE is not an emulator (hence, the recursive name Wine Is Not an Emulator).  It provides a loop device from which the programs you are running can hook Linux APIs.
 
 That all will be invisible to you while using WINE, but it is worth understanding.  That's why NightwishFan used the term "natively".

Using a pre-existing partition in a virtual machine like VirtualBox is so fraught with the potential to screw up both the host and guest OS that I would highly recommend against it unless you are very experienced.  A good IT professional might do it, but it would not be worth the risk to your personal machine.

---

### Post by RedRat on 2010-03-15
Very definitely give WINE a try. I run my favorite thumb-nailer, ThumbsPlus, under WINE and I find that it actually can rename files (using the Auto-Rename function) faster than some native Linux apps. In order to get some Windows programs to operate under Wine, you may have to visit the Winetricks web site ([http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks))
to get your programs to run reasonably free. 

You sill definitely want to check out the Wine website to ensure that whatever Windows program you want to run and your particular Linux distro are compatible. Research before installing is always a good idea and saves wasted effort.

---

