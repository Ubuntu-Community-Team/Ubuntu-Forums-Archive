---
title: "Cannot burn DVDs"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by coblenis on 2009-06-01
Hello,

I cannot burn DVDs in Ubuntu 9.04.  I have tried Brasero, GnomeBaker, the built-in CD/DVD Creator, and K3b.  I think the problem is "failed with SK=5h/WRITE PROTECTED" 

I have frigged with the permissions.  I can read and write, the cdrom group has read and write permissions for the .iso, and I think I set the write authorizations through System->Authorizations.  What do I have to do so I can use my burner? 

> System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-11-generic
Devices
-----------------------
Slimtype DVD A  DS8A1P CH71 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD+R Dual Layer

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: splitting layers at 1412000 blocks
:-[ SEND DVD+R DOUBLE LAYER RECORDING INFORMATION failed with SK=5h/WRITE PROTECTED]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2824000 -dvd-compat -speed=2.4 -use-the-force-luke=bufsize:32m 



I have an HP DV6608ca laptop with a Super Multi 8X DVD±R/RW with Double Layer Support disc drive (DVD A DS8A1P).

---

### Post by mikechant on 2009-06-01
You may have tried or thought about these things already, but:

a) Are you absolutely sure the 'blank' disc you are using is really blank? As it is a write-once disc if it's been used you won't be able to reuse it. I have heard cases of supposely blank discs out of a sealed packet actually containing data.

b) You appear to be using a double layer disc (which your drive says it supports) but have you tried a single layer disc?

c) Have you tried a different brand of disc? Some drives just don't work with some disc brands (although this is uncommon nowadays).

---

### Post by coblenis on 2009-06-01
I did a little more research on the DVD burner.  I thought it was an OS issue because I was able to write to CDs, CD-RWs, DVD-RWs in Windows without a hitch.  According to what I found, this particular burner has a lot of compatibility issues and is only fully functional with Verbatim discs.  I'm burning an .iso with the Verbatim DVD+R DL 2.4x and so far, so good. 

Thanks for the direction.

---

### Post by LewRockwell on 2009-06-01
great to hear!

remember to pay-it-forward!

---

### Post by spiner on 2009-06-05
Hi there.

Sorry if I move a little bit out from the thread subject, but perhaps you could help.

I have an Asus X51RL laptop with the same DVD drive and I'm not able to install Ubuntu 9.04 as the DVD drive is not recognized (it just boots, loads the kernel and then says "No common cdrom drive was detected"); if I do a network upgrade (therefore without using the DVD drive) everything goes well but in the end the system is not able to find the DVD drive if I try to access it.

Can you give some hints how you succeded to use that DVD drive with 9.04?

Thanks!

---

