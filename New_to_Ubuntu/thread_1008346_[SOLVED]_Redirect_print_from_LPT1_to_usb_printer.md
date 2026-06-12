---
title: "[SOLVED] Redirect print from LPT1 to usb printer"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Bladeforger on 2008-12-11
Hi:

I am slowly but surely converting over to Linux, using Ubuntu.  (Actually it's Kubuntu with Gnome to take advvantage of KPowerSave).  I have some old DOS software that is indispensible.  It's an old accounting package that is absolutely bulletproof, and I know it inside and out.  I don't want to exchange it for something else that I don't know.

BTW, this is on a NEW computer that is sitting next to my old Windows box until all the kinks are ironed out.

The software is currently runnable under Win4Lin, and I'm running it there to  see how it works.  Problems are two:

1. It wants to print to LPT1.  I could probably get a card for parallel, but that's a 50 buck expense.  On the Windows box i used a piece of software called DOS2USB.  It doesn't seem to work well with Win4Lin.  Is there a way to make Linux recognize output that is trying to go to LPT1 and just redirect it to the USB printer?  Would that work for a DOS program  being run under Win4Lin?

2. Is there a better way to run a DOS program than through Win4Lin?  I get a really small DOS screen, which is probably something I can fix somehow with resolution.  Would DOSBOX  be better?  Is it do-able with WINE?  Surely someone can guide me down the best path.

Thanks, one and all, in advance, for your assistance!!!

Keith

---

### Post by Bladeforger on 2008-12-18
Still waiting... anyone know the answer???

---

### Post by bwang on 2008-12-18
What program are you trying to get to work?

---

### Post by donkyhotay on 2008-12-18
I've never had a problem specific to USB printers on linux. If you go to system > administration > printers it should show and recognize all printers connected to your system regardless of whether they are connected through the parallel or USB ports. If it doesn't what happens when you click on new printer?

---

### Post by Bladeforger on 2009-01-07
> **bwang said:**
> What program are you trying to get to work?
Aha!  Good question!   As Donkyhotay noted, a USB printer works fine and dandy for Linux... and this isn't Linux or Ubuntu software--it's DOS software.  I've tried kinda running it under Win4Lin with the Windows install (which creates, I guess, the right pif file for the old DOS).

As I've learned, to my chagrin, Win4Lin doesn't always play well with USB devices.

I went out and bought a new laser printer with a parallel port ... and a parallel port card.  Got those installed.  What with Christmas and New Years, I haven't gotten back around to futzing around with stuff... but Win4Lin still doesn't like my printer too much.  LUCKILY, the tax return software has a PDF option and it's working fine.  The old DOS software will print to a text file, but there are other problems.  (And everything else I do can be done under Linux somehow / someway.  Yay!!! (or with Wine as in the case of my ancient Quicken 1999))

FWIW, Win4Lin was the only thing I found that would read the install disk and install my ***super-picky*** tax software.  I tried Wine and Crossover Office, to no avail.

I'm going to mark this as solved; however, it's only partially solved.  I bought a parallel port and a different printer to solve the problem, and that won't even totally fix things.  My workaround is a combination of PDF printing and printing to a text file.  

What I was looking for was either some software utility or some script that would "listen" for output to a nonexistent LPT1 and, upon finding it, redirect it to the USB printer.  Under Windows XP, I had this software (dos2usb) that did this and it only cost ten bucks.  I thought about trying it under the XP running on Win4Lin, but it was going to cost me another ten bucks, and I have other issues with the DOS software running the way it is.  That's for another post.

---

