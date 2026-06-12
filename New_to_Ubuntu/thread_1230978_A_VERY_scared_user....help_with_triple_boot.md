---
title: "A VERY scared user....help with triple boot"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by aperture123 on 2009-08-04
Hi, I recently aquired a netbook and love it!:o An acer aspire one with xp already installed (including all the crap:P). I downloaded ubuntu netbook remix, ran it from usb, and all went well. However, I made the mistake of going into desktop mode and installing compiz fusion, which argues with maximus, causing no menu bars.....I paniked and uninstalled ubuntu netbook remix, skrewed up my bios, reinstalled, accidentally deleted xp, then (after a long time) reinstalled xp (overwriting ubuntu). back to square one. Now, I'd like ubuntu netbook remix, windows 7, and windows XP, but I do not know how to go about doing this. i currently ONLY have xp installed......should I install windows 7, then ubuntu UNR, or UNR then windows 7
:confused:

---

### Post by mgranet on 2009-08-04
The Windows bootloader does not like to play nice with other operating systems, so you should instsall XP, Vista, then UNR. That way, you end up with the GRUB bootloader, which will see all operating systems.

---

### Post by snowpine on 2009-08-04
1. You can install Ubuntu inside Windows using Wubi. 
2. You can install VirtualBox (or similar) in Windows to run Ubuntu inside a virtual machine. 
3. You can run Ubuntu from an SD card or USB flash drive.

In other words, you do not need to partition or dual boot to use Ubuntu, if you are scared. Take your time and read up on the subject before proceeding.

Sorry but I do not know much about Windows 7...

---

### Post by mgranet on 2009-08-04
I don't think VirtualBox would be an ideal solution for a netbook. The thing would crawl, if it would run at all.

---

### Post by JIMIneitor on 2009-08-04
Id say:


1. Grab this 

[DBAN]("http://mirrors.vanadac.com/sourceforge.net/projects/dban/files/dban-beta/dban-beta.2007041900/dban-beta.2007042900_i386.zip") is for totally wiping off your HD, repeat, totally.


2. Get the Ubuntu liveusb, and partition your HD as desired

3. Install either XP or 7, whatever you want first.

4:Install XP or 7.

5. Install Ubuntu.

6. Youre ready to go :D

---

### Post by MikeTheC on 2009-08-04
Oh, I thought you were very scared by this...

[img]http://file23magazine.files.wordpress.com/2009/06/michael-jackson-thriller-remake-acapella-5.jpg[/img]

So sorry.

---

### Post by snowpine on 2009-08-04
VirtualBox runs fine on a netbook, don"t be silly. :)

The OP is scared to partition, so I was simply pointing out various alternatives.

Here is some good reading material: 
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by mgranet on 2009-08-04
@ MikeTheC:
Is there a facepalm button?

---

### Post by aperture123 on 2009-08-04
Ok, so far...
"you should instsall XP, Vista, then UNR" by Mgranet
I'm installing Windows 7, not Vista, and windows 7 comes with its own bootloader...

Regarding multiple posts on a vitual box:
Thanks, but no thanks, I'm scared, but not that scared, I'd still like the full experiance of Windows 7, XP, and Ubuntu:D

"Oh, I thought you were very scared by this..."
......of no relevance to this topic......:confused:

Oh, and No I will not get rid of XP, I totally messed up the boots like 10 times and each time had to redo XP until I finallly got it right. Then had to install drivers.....games......programs.....:(

While looking online I found a question similar to mine...I guess what I'm saying it, should I install windows 7 first, or ubuntu? Windows 7 comes with the bootloader for XP and 7 and ubuntu GRUB bootloads Windows 7 and Ubuntu.....so its like a dual boot dual boot, which I'm fine with.....should that work out okay, or will my computer not know whats going on:confused:
BTW: Thanks very much for replying so fast!:D

---

### Post by JIMIneitor on 2009-08-05
i think that GRUB should take care of everything just fine.

As long as you dont install any windows before GRUB, youll be ok!

---

### Post by LewRockwell on 2009-08-05
> **JIMIneitor said:**
> i think that GRUB should take care of everything just fine.

As long as you dont install any windows before GRUB, youll be ok!

not true

installing windows will alter your MBR by removing the grub and replacing it with the MBR that windoze likes

there are several tutorials on the interwebs which describe what you want to do step by step

.

---

### Post by t0p on 2009-08-05
> **JIMIneitor said:**
> Id say:


1. Grab this 

[DBAN]("http://mirrors.vanadac.com/sourceforge.net/projects/dban/files/dban-beta/dban-beta.2007041900/dban-beta.2007042900_i386.zip") is for totally wiping off your HD, repeat, totally.


Holy cow!  You do *not* need to use DBAN!!

[Darik's Boot And Nuke]("http://www.dban.org/") is a utility for **secure deletion of disks** - it's a program you'd use if you wanted to wipe all data from a hard drive and wanted to be sure that no one would be able to recover any of the data.  [www.dban.org]("http://www.dban.org/") describes it as "an appropriate utility for bulk or emergency data destruction".

All the OP wants to do is to repartition his hard disk.  For the OP's purposes, **gparted** is the appropriate program to use. 

If anyone reading this *is* interested in secure deletion/"emergency data destruction", DBAN is an appropriate program to use.  But there are other options.  I recommend checking out [this site]("http://mirror.href.com/thestarman/asm/mbr/WIPE.html") - it explains in detail what secure deletion actually means, what data recovery software is able to do, and what you can do to ensure that no one can retrieve the files you have chosen to destroy.

**JIMIneitor**: I realise you are trying to be helpful, but I don't think it's a good idea to point a newbie in the direction of a program like DBAN when that isn't the kind of program the newbie actually wants!  **Darik's Boot And *Nuke*** - the clue's in the name!  :)

---

### Post by Jerry N on 2009-08-05
I just completed an experimental triple boot installation on a desktop machine with a 160gb HD.  I used Parted Magic 4.3 to create 4 partitions:  (1) 40 gb NTFS (2) 40gb NTFS (3) 70+gb EXT3 (4) Remainder as Linux swap.  I installed XP on the first 40gb partition, made sure it worked, and installed Win7 RC on the second 40gb partition.  This gave me dual boot Win7 and XP.  I then installed Ubuntu 9.04 on the EXT3 partition, using the manual partition option.  In all cases I elected NOT to reformat the drive during installation.  On boot-up, Grub now gives me the choice of UBUNTU or a Windows boot manager.  Selecting the Windows boot manager then gives me the choice of Win XP or Win 7.  All works fine and it was really quite easy to do.  

Jerry

---

