---
title: "Problems erasing and writing DVDs"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by marktyler on 2009-01-19
I'm having problems writing and erasing DVD-RW disks written in compatible mode by OSX - the DVD player reads them ok. I'm running 8.04 (upgrade from 7.04 which also experience the problem).

Neither my Sony DW-U14A or my LiteOn DVD writer will erase or write to these disks. The LiteOn doesn't even register them now although I get the green light on the front of the drive. K3B shows "No medium present". I think the drive may be screwed but that still leaves the Sony.

In K3B or Brasero I get a write error on the Sony. K3B used to work. I've therefore had to write DVD-RW disks using my Mac (the linux box is a file server). If I try to erase a disk that was written by the Mac it says it's erased it but then the data structure is still intact. 

Not sure what's gone wrong. Normally I'd reinstall the OS but this machine has all my RAID setup, webmin etc so I'd prefer to find and fix.

K3B output from a format was...

> System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-23-generic
Devices
-----------------------
LITE-ON DVDRW SHW-16H5S LS0N (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

SONY DVD RW DW-U14A 1.0d (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite]
dvd+rw-format
-----------------------
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD-RW media in Sequential mode detected.
:-[ PERFORM OPC failed with SK=5h/ASC=30h/ACQ=08h]: Wrong medium type
:-[ BLANK failed with SK=5h/ASC=30h/ACQ=08h]: Wrong medium type

dvd+rw-format command:
-----------------------
/usr/bin/dvd+rw-format -gui -blank /dev/scd1 

Changing the form options didn't change the result. I would have thought that force format from K3B would do the job - maybe I misunderstand DVD-RW formatting?

---

### Post by billgoldberg on 2009-01-19
Not answering your question:

**usb stick**

---

### Post by marktyler on 2009-01-19
> **billgoldberg said:**
> Not answering your question:

**usb stick**

I have heard of such a device. Unfortunately the disks are for use in the DVD player as they get populated with divX encoded AVIs. So, whilst I use USB sticks for other things, it's DVD-RW disks here (I don't use DVD-Rs as once the movies have been viewed then they don't need to be kept on plastic).

---

### Post by gn2 on 2009-01-19
Why not completely blank the discs with OS-X first then try writing to them in your Ubuntu machine?

---

### Post by marktyler on 2009-01-20
> **gn2 said:**
> Why not completely blank the discs with OS-X first then try writing to them in your Ubuntu machine?

As I want to find out why and/or solve the problem of why my Ubuntu install can't blank them this is not what I'm asking. (Incidentally write and re-write under OSX is what I'm currently doing)

Is it expected behaviour because of something OSX does to the disk even though my DVD player is ok with them?
Is it a failing in my linux install?
etc

I look at these things as part of the learning process of living with Linux, but thanks for the suggestion.

---

### Post by gn2 on 2009-01-20
I've no idea about OS-X, but if you use it to totally blank a DVD-RW then try it in Linux and it works, you'll have determined that "compatibility mode" (whatever that is) in OS-X is the culprit.

---

### Post by marktyler on 2009-01-20
> **gn2 said:**
> I've no idea about OS-X, but if you use it to totally blank a DVD-RW then try it in Linux and it works, you'll have determined that "compatibility mode" (whatever that is) in OS-X is the culprit.

Absolutely. I can also understand why, if this is the culprit, linux could not blank the disk. Do I misunderstand things or should it not be able to reformat it though? Especially with the force option selected.

---

