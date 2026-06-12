---
title: "&lt;Sigh!&gt;"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by PatManOz on 2008-12-27
Windows Vista HP SP2.

Yesterday I downloaded 8.04:
Hardware testing was fine except for the video test - no bars or snow.
I 'visited' all hard drives, CD drives and a USB drive - opened/played various mp3/wma/mp4 files.
Installed inside Windows (drive D).
On boot, system hung:
[INDENT][BusyBox v ....]
Type 'help' ...
(initramfs) _[/INDENT]

Then I could not uninstall .....
Manually uninstalled and cleaned up (I understand Windows)

Yesterday I downloaded 8.10:
Hardware testing was fine except for the video test - no bars or snow.
I 'visited' all hard drives, CD drives and a USB drive - opened/played various mp3/wma/mp4 files.
Installed inside Windows (drive C).
On boot, system hung:
[INDENT]Booting GRLDR...
_[/INDENT]

<Sigh!>

Any suggestions welcomed ......

---

### Post by halitech on 2008-12-27
personally I would forget about using wubi/live cd with vista. use the vista tools to shrink your partition and create space for ubuntu then do a manual install with the alternate install cd and point it to the empty space.

more info here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by albinootje on 2008-12-27
> **PatManOz said:**
> 
On boot, system hung:
Booting GRLDR...

The Ubuntu installation cdrom should be able to do the resizing for you during the install.
After the installation you should be able to boot both Ubuntu and Windows.

If you run into problems with that (not very likely), then use the gparted live cdrom.

---

### Post by PatManOz on 2008-12-28
I do believe I am getting a message - Ubuntu is every bit as good as Windows, but they should be served on separate plates ...

Ok! I will give it a go - Thanks to both of you.

---

### Post by PatManOz on 2008-12-29
Ok! I have most of it unravelled.

The problem is that (Windows + Me) is MUCH more reliable than (Ubuntu + me).

With that in mind, I would prefer to boot via Windows. That leaves the Boot sector untouched and uses Windows BCD (Boot Configuration Data store) to select the OS.

I would then be very happy to play Ubuntu.

At the moment my System boots directly into GRUB, with the default system Ubuntu. I am unwilling to play here because if I mishandle Ubuntu, I also lose access to Windows.

How may I STOP the default boot to Ubuntu?

---

### Post by albinootje on 2008-12-29
> **PatManOz said:**
>  The problem is that (Windows + Me) is MUCH more reliable than (Ubuntu + me).

With that in mind, I would prefer to boot via Windows. That leaves the Boot sector untouched and uses Windows BCD (Boot Configuration Data store) to select the OS.

I would then be very happy to play Ubuntu.


Several people on this forum recommended this software for booting from MS-Vista : [http://en.wikipedia.org/wiki/EasyBCD](http://en.wikipedia.org/wiki/EasyBCD)

I don't use MS-Windows, so I suggest to gather some more information about this software + usage first.

---

### Post by thunk77 on 2008-12-29
> **PatManOz said:**
> Ok! I have most of it unravelled.

The problem is that (Windows + Me) is MUCH more reliable than (Ubuntu + me).

With that in mind, I would prefer to boot via Windows. That leaves the Boot sector untouched and uses Windows BCD (Boot Configuration Data store) to select the OS.

I would then be very happy to play Ubuntu.

At the moment my System boots directly into GRUB, with the default system Ubuntu. I am unwilling to play here because if I mishandle Ubuntu, I also lose access to Winwows.

How may I STOP the default boot to Ubuntu?

Problem is that windows boot loader is not very cooperative with non-microsoft operating systems:P

I think that there's a utility for vista (assuming that is what you use) called "vista boot pro" where you can edit the vista bootloader, but i think that you would be way over your head with that one.

I don't understand why you can't just select windows from the grub menu when you boot?

---

### Post by albinootje on 2008-12-29
> **thunk77 said:**
>  I don't understand why you can't just select windows from the grub menu when you boot?

See the error description in the initial post of the OP.

---

### Post by PatManOz on 2008-12-30
Ok Guys! Thanks for your continued support.
I have:
[INDENT]Rebuilt Master Boot Record (Vista)
Rebuilt Boot Sector (Vista)
Modified partition sizes for Ubuntu
(and deleted it in the process)
[/INDENT]So now Windows is Windows is Windows.
What I need to do (if I understand it correctly) is to re-install Ubuntu, ensuring that Grub is loaded into the boot area of the Ubuntu PARTITION
and not the MBR of the C: drive.
That way I can (accidently) destroy (and rebuild) Ubuntu without prejudice.
I will use EasyBCD to to modify the Vista BCD to allow a chainload to Ubuntu.
1. Any advice on the install would be appreciated
2. Thanks again for the support

---

### Post by steveneddy on 2008-12-30
All the cool kids are partitioning and dual booting this year.

You don't want to be left out, do you?

IMHO - Wubi sucks.

Partition the HD and install it on the HD.

You won't get a good experience until you do.

If it were my PC I would wipe Windows and just use Ubuntu.

---

### Post by luisito on 2008-12-30
I think you should go back to booting with grub if you ever want things to work well.

The way linux set up things is the following. In the MBR (Master Boot Record) you have GRUB, which loads the operating system of your choice. Then you have Ubuntu in one partition and Windows in the other. If you screw up Ubuntu big time, the worst that can happen is that you can not boot on Linux any more, but you can still boot on Windows. The system would become unbootable only if you screw up GRUB which is certainly possible but highly unlikely. When you select Windows in the GRUB menu, you never load the linux kernel.

---

### Post by PatManOz on 2008-12-31
Thanks Guys - I am Home and Hosed (i.e. with my pants on!)!!!!

The page I REALLY needed was at:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

I can now dual boot via Windows Vista (Safest for ME!).

Ubuntu boots from its own partition.

GRUB offers me the 4 standard Ubuntu options, PLUS boot back to VISTA.

Exciting times ahead.

Thank you all again!!

**<Sigh - Relief!!!!>**

---

### Post by PatManOz on 2008-12-31
> **thunk77 said:**
> ...you can edit the vista bootloader, but i think that you would be way over your head with that one.


Over my head? No Way!!

---

### Post by PatManOz on 2008-12-31
> **albinootje said:**
> ...for booting from MS-Vista : [http://en.wikipedia.org/wiki/EasyBCD](http://en.wikipedia.org/wiki/EasyBCD)


Many thanks - a very easy tool to use.

---

### Post by PatManOz on 2008-12-31
> **halitech said:**
> personally I would forget about using wubi/live cd with vista. use the vista tools to shrink your partition and create space for ubuntu then do a manual install with the alternate install cd and point it to the empty space.

more info here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Excellent advice - valuable site - thank you.

---

