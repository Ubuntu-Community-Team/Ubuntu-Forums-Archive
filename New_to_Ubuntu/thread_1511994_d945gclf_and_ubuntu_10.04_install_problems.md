---
title: "d945gclf and ubuntu 10.04 install problems"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-06-17
Well I have a d945 GCLF and 2gigs of ram, with the MB comes a atom processor.

I can not get the I386 Ubuntu 10.04 Desktop Live Cd to work well.

Many errors/slow speed in everything/ sometimes boots sometimes does not/ try to install, but it fails or freezes or give a error 5 I/o error.

The HD is a WD 80 gig 7200 RPM, both on Sata

Do not know what the main problem is, but it is very disturbing and annoying.

Anyone know a fix or perhaps some things I can try?

---

### Post by cariboo on 2010-06-17
Run a disk integrity check from the menu on the Live CD. I have a similar system that I've run everything from Intrepid to Karmic on, both 64-bit and 32-bit, I'm Currently running XBMC Live, and have never had a problem.

---

### Post by ericeclifford on 2010-06-17
> **cariboo907 said:**
> Run a disk integrity check from the menu on the Live CD. I have a similar system that I've run everything from Intrepid to Karmic on, both 64-bit and 32-bit, I'm Currently running XBMC Live, and have never had a problem.

Well I did the disk check off the menu on a different machine( a better one, nicer mb, nice graphics card, about same ram)
It boots fine on this machine, and the USB version does as well

When I tried the USB on the machines ( tried 4 different machines, all with the same setup, all work on 8.04 live/USB/hard drive installation) and it returns with a black screen and text in the top left hand corner saying
"Boot Error"
.


So, it is confirmed, that this MB, I guess does not work at all with 10.04, which is very annoying, because I need this OS to load on all of these machine( i have like 25 of them) because the old ubuntu versions do not hold a wireless connection, and that is very important for my business.


Anyone know a solution for this?

---

### Post by pharnet on 2010-10-20
You may want to check that you have the IGD Aperture size set at 256MB rather than 128MB in the BIOS. Solved some odd problems for me with this motherboard.

---

