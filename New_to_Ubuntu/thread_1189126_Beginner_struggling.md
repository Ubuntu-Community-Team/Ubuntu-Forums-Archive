---
title: "Beginner struggling"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by gargoyle60 on 2009-06-16
[SIZE=2]Firstly, I am an absolute beginner to Linux. I have chosen ubuntu because I have heard that it is quite easy to use![/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I want to try it on an old Windows98 PC, with very low spec. and hopefully dual boot.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Specification:
- PC100 motherboard (PC100 "PC-Chips Motherboard M726")
- BXcel chipset
- Pentium II 350 MHz
- 4GB Hard Disk (partitioned via DOS FDISK into two x 2GB partitions, with the first partition running Windows98 and the second partition left unformatted ready for Linux)[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Some initial problems:
1. my keyboard is a 104-key compatible PC AT having a connector with five pin AT standard DIN with a small notch on the rim opposite the five pins. It is not a PS/2 connection.
2. my three button mouse is a serial mouse connected to the COM1 port. How do I identify to Xubutnu that I am using a serial mouse on the COM1 serial port? Does it involve using some utility (if yes then what/where/how?) or defining the details in a configuration file somewhere (if yes then what/where/how?).
3. I tried using FIPS to split the original partition and it knackered my disc; luckily I recovered using a ROOTBOOT.000 file. I had to reinstall Windows98 on the first partition.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Because of the low spec I have tried installing both Xubutnu 7.10 or Xubutnu 9.04 using a standard desktop iso download. In both cases the mouse just didn't work at all. When the desktop did display, I couldn't navigate to anything (no mouse) using the keyboard, apart from Ctrl+Alt+Backspace and Ctrl+Alt+F4 and Ctrl+Alt+F7, etc.[/SIZE]
[SIZE=2]Incidentally, when I tried installing Xubutnu 7.10, a message briefly appeared saying something along the lines of "chipset not recognised". This didn't happen with Xubutnu 9.04.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I appreciate that somewhere I'm going wrong, perhaps in my entire approach, and that maybe my machine is simply too low spec to ever get a desktop running under Xubutnu. Or perhaps I've downloaded the wrong iso file.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Thoughts and advice appreciated.
Thanks
Gary
[/SIZE]

---

### Post by shifty_powers on 2009-06-16
the first thing that would concern me is amount of ram in the machine. Realistically you need at least 128mb for even Xubuntu.

that machine really is quite old.

Maybe you should look up something like puppy linux or dsl linux. (google them).

---

### Post by kestrel1 on 2009-06-16
> **shifty_powers said:**
> the first thing that would concern me is amount of ram in the machine. Realistically you need at least 128mb for even Xubuntu.

that machine really is quite old.

Maybe you should look up something like puppy linux or dsl linux. (google them).
I agree with this & would also suggest using Puppy Linux:
[http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by scrooge_74 on 2009-06-16
I would go with DSL linux, that machine is way to old for a big distribution. Also a net install of Debian, but is easier if you go with DSL which I feel has more tools than puppy

---

### Post by ymra on 2009-06-16
My suggestion is to use a linux distro specificaly created for use on old hardware such as deli linux ([http://www.delilinux.de/](http://www.delilinux.de/)) or vector linux light ([http://vectorlinux.com/news/vectorlinux-light-edition-released](http://vectorlinux.com/news/vectorlinux-light-edition-released))

You will have far fewer headaches.

---

### Post by blazemore on 2009-06-16
Have a look at CrunchBang Linux.
It's based on Ubuntu, but is very lightweight.

---

### Post by Therion on 2009-06-16
That system is barely meeting minimum specs for Ubuntu:> **Bare Minimum requirements**

It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the Alternate install CD to attempt such an installation.

    * 300 MHz x86 processor
    * 64 MB of system memory (RAM)
    * At least 4 GB of disk space (for full installation and swap space)
    * VGA graphics card capable of 640x480 resolution
    * CD-ROM drive or network card 

Look at Damn Small Linux instead:  [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Sir Jasper on 2009-06-16
Hi,

Damn Small Linux (DSL) is based on Knoppix is about 50 MB download.

Version dsl-4-4.10-embeded works from my W98SE hard drive or directly from a flash stick. It can be run from within W98SE, using Ctrl + Alt switches between 98 and DSL (and vice versa). If it works it works in this way it will almost certainly be not just slow but incredibly slow - but at least you can try easily.

If it works, it may run quite quickly if you can run directly from a CD.

I also have Knoppix both CD and DVD (with 8 GB of compressed programs). Knoppix configures everything (except my ancient scanner) perfectly as it loads. DSL should do the same but I only tried DSL briefly out of interest.

I have triple boot with W98SE, Xubuntu and Ubuntu all working really well but I have plenty of RAM (640 MB) and lots of hard drive space.

Let us know how you get on and for sure post back if you have a problem.

My regards

---

### Post by gargoyle60 on 2009-06-16
Thanks for all the recommendations, I will reconsider.
 
I have the standard Windows98 rather than 98SE and yes it is an old PC (1998'ish).
 
I forgot to mention RAM - 256MB total. Given that I managed to at least get some way into the installations, I suspect that it may still be possible although it will run like a snail.
 
I suppose the main problem still relates to the serial mouse. 
Any suggestions?

---

### Post by LewRockwell on 2009-06-16
[http://www.puppylinux.org/downloads/official-releases/puppy-linux-421](http://www.puppylinux.org/downloads/official-releases/puppy-linux-421)

[http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)

Puppy is 100mb and DSL is 50mb

Download the ISOs and burn them both as slow as you can

They both will "live-run" and they install and re-install easily so if you break them, no problems.

Also, while you're at it you might as well burn one of these to check out:

[http://partedmagic.com/download.html](http://partedmagic.com/download.html)

Here the object is a nice assembly of programs for setting-up/rescuing/recovering machines

That should keep you busy for awhile

ps-I'm running DSL on a 1997 Gateway laptop with a 150mhz processor, 224mb ram, 3gb hard drive, netgear 10/100 PCMCIA lancard

enjoy!

---

### Post by Sir Jasper on 2009-06-16
Hi again,

As you seem to have broadband I'd suggest downloading and making a Knoppix CD. Then run it live - there is a good chance it will even auto configure your mouse properly (and it doesn't need a hard drive except, perhaps, to save any settings and data). I'm sure your RAM is fine but whereas Xubuntu should be OK, I think its minimum installation size is about 1.5 GB and with 256 MB RAM I think you'd need a Swap partition as well.

My regards

If you just want a virtually infection free environment you could settle on say, Linux browser and email and continue using win98?

My regards

---

### Post by scrooge_74 on 2009-06-16
I wouldnt advice a Knopix CD, the distro that runs is a full KDE enviroment which could still be too much for the specs of that PC. He needs to use a light distro like puppy or DSL

---

### Post by Sir Jasper on 2009-06-16
Hi Scrooge,

You may well be right, but a few coins spent on a download and a blank CD "may" prove invaluable and Knoppix may auto configure the problematic mouse and may run well with 256 MB RAM. A Knoppix DVD might then be the next step if the CD works.

My regards

---

### Post by scrooge_74 on 2009-06-16
Knoppix is a great distro, but I feel is going to be too much for the little machine, remember the specs are pretty low, probably Knoppix would take ages to boot (I would proly kill myself waiting for it to boot), I imagine the CD drive is pretty slow and I doubt it even reads DVDs.

---

### Post by Sir Jasper on 2009-06-16
Scrooge,

They can't fight you if you kill yourself.

I'd be disappointed if took more than 5 minutes to load but amazed if more than 10. However, my own experience with a 1998 machine with more RAM may or may not be replicated.

My regards

---

### Post by scrooge_74 on 2009-06-16
You are right on that one, better just throw the PC out the window then :D

Load speed will depend on the CD-rom if the darn thing is like 4x is goin to take a while :D

---

### Post by gargoyle60 on 2009-06-17
Thanks once again for all the input.
 
My CD drive (read-only) is rated at 54x and no it doesn't handle DVDs.
 
DSL looks to be my best bet so far, although if I can find enough time in a few weeks then I may try some of the other suggested distros.
 
I have been reading one particular book that suggested my PC could (?) handle a low-load Linux distro, but then again it was an old and very generalised book (ISBN 0-7645-3593-5) and referred to early Red Hat but had lost its accompanying CDs so I couldn't actually try that distro.
 
I do have another PC - XP 3GHz, 1GB RAM, 80GB disc - so later this year I may convert that to Linux. I wanted to experiment with my old PC first, that was my initial plan and that was the only reason for using such a low-spec machine.
 
C'est la vie!

---

### Post by Sir Jasper on 2009-06-17
Hi,

If you would like to PM me with your address I'll send you a CD version of Knoppix. You may be delighted with it. 

Foolishly, I hadn't realised that Scrooge was referring to the CD read speed.

My 1998 computer runs superbly well and quickly - it can calculate the first 5,000,000 + prime numbers and save them in less than 4 seconds. Just because "your" computer can't quite reach 118,000,000,000 instructions per second (which I think is the current record) ..............

---

### Post by longtom on 2009-06-17
I struggled with puppy linux on some hardware (old Toshiba laptop comes to mind).

However, I haven't found anything easier to install and run on an old system again and again and withoud failing me once - and that would be [SliTaz](http://www.slitaz.org/en/).

Having said that, I also had considerable success with Debian Stable and the non GUI setup.  That would give you a bit more software options - depending what you plan to do with that oldtimer of yours.

Good luck

---

### Post by Bölvaður on 2009-06-17
I realise that the computer is extremely slow but here are my thoughts.

I installed xubuntu on a similar machine some time ago, it had 128 MB ram so I had to download the **Alternate install cd** (not the live cd). The install will work and all standard mouses and most if not all USB mouses should too.... ahhh... if the usb hub is recognised... this is an old hardware which might not be from a reputable manufacturer that supports linux or is too rare for the linux community to support the hardware.... plush this is very old hardware so it might have been dated before the internet and super computers began to run almost only on linux.

But even with xubuntu, this computer will be "quite sluggish", but it may give you a (tiny bit (Im trying to not offend anyone here)) better experience than Damn Small Linux (DSL)

---

### Post by gargoyle60 on 2009-06-17
I think before I try anything else I'm going to install some more memory, up to 768MB is possible on my old PC. I've got some spare RAM somewhere...

---

### Post by jim Kane on 2009-06-17
> **gargoyle60 said:**
> Thanks for all the recommendations, I will reconsider.
 
I have the standard Windows98 rather than 98SE and yes it is an old PC (1998'ish).
 
I forgot to mention RAM - 256MB total. Given that I managed to at least get some way into the installations, I suspect that it may still be possible although it will run like a snail.
 
I suppose the main problem still relates to the serial mouse. 
Any suggestions?

                                       i run puppyLinux on an ancient PC with DIN keyboard and USB mouse via a usb-pci card
    [LEFT]256Mb ram and 600mg processor[/LEFT]
    [LEFT]works fine, quicker then win98.  



mike
[/LEFT]

---

### Post by LewRockwell on 2009-06-17
> **jim Kane said:**
> i run puppyLinux on an ancient PC with DIN keyboard and USB mouse via a usb-pci card
    [LEFT]256Mb ram and 600mg processor[/LEFT]
    [LEFT]works fine, quicker then win98.  



mike
[/LEFT]

I've still got running machines with hard drives too small to install Damn Small Linux...lol.

---

### Post by gargoyle60 on 2009-09-09
Yippee! 

Update:
I've managed to get DSL installed on my hard drive with Grub (Lilo didn't work, grub did!).
At least I can use my old serial mouse and also mount the Windows file system, so some progress at last.

Once I can establish a full and stable DSL installation I can tailor my old PC and then perhaps move up to xubuntu or similar.

---

### Post by gargoyle60 on 2009-09-15
Update 15-Sep:
Astonishingly I've managed to successfully install xubuntu 6.06.1 using the alternate CD.
However, my serial mouse still isn't being recognized. Strange that DSL recognized it, but not xubuntu.

---

### Post by Sir Jasper on 2009-09-15
Hi,

Thanks for your update and good to know you are on a winning trail.

My regards

---

### Post by steveneddy on 2009-09-15
> **Therion said:**
> **That system is barely meeting minimum specs for Ubuntu:**

Look at [COLOR=Blue]**Damn Small Linux**[/COLOR] instead:  [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Perfect suggestion.

I have machines like that at home and they run DSL just fine.

I have a 486 that runs DSL for that matter.

---

### Post by k33bz on 2009-09-15
> **ymra said:**
> My suggestion is to use a linux distro specificaly created for use on old hardware such as deli linux ([http://www.delilinux.de/](http://www.delilinux.de/)) or vector linux light ([http://vectorlinux.com/news/vectorlinux-light-edition-released](http://vectorlinux.com/news/vectorlinux-light-edition-released))

You will have far fewer headaches.

There is not much to offer as far as installing software with delilinux. It is a good OS, for older Computers, but not much in their own repo and alot of things are hard to install to it. It is not like other flavors.

---

### Post by afroman10496 on 2009-09-15
One word: [http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Lubuntu-50492.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Lubuntu-50492.shtml)

---

### Post by gargoyle60 on 2009-09-18
[FONT=Arial][SIZE=2]Lubuntu - never noticed that before. Hmm, interesting.

 Anyway, I have since managed to get my old serial mouse working under Xubutntu 6.06.
 For the benefit of anybody else with a serial mouse, this is how I succeeded - [http://ubuntuforums.org/showthread.php?t=225595](http://ubuntuforums.org/showthread.php?t=225595)
[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
   :)

---

