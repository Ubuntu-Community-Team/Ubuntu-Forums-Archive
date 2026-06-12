---
title: "Synaptic Packages via USB?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by psychlopath on 2009-11-12
I'm having some nasty problems trying to get the wireless on my Aspire One to work.  Not having a wired connection to use is making things tough.

When I try to have hardware drivers used, the process locks.

SO, I did a search and found that installing some packages should help me be able to use the drivers.

Problem is, Synaptic asks for the Live CD.  I only have a USB drive.  

Is there a way to fool the machine into thinking the jump drive is a CD drive?

---

### Post by ukripper on 2009-11-12
use ubuntu live usb then. [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

---

### Post by mrboojive on 2009-11-12
> **psychlopath said:**
> I'm having some nasty problems trying to get the wireless on my Aspire One to work.  Not having a wired connection to use is making things tough.

When I try to have hardware drivers used, the process locks.

SO, I did a search and found that installing some packages should help me be able to use the drivers.

Problem is, Synaptic asks for the Live CD.  I only have a USB drive.  

Is there a way to fool the machine into thinking the jump drive is a CD drive?

All the package files are included on the Live USB in the "pool" folder. If you know what packages you need to install, you should just be able to go to your USB drive, go to the "pool" folder, then probably go to the "restricted" folder (where restricted drivers are), find the appropriate ".deb" files, and double click on them to install.

---

### Post by psychlopath on 2009-11-12
UKRipper:  This is what I'd done and how I've been installing onto my acer.  It's really a great idea.  However, when I go in to edit edit the sources, I cant figure out how to to get the USB to appear as if it's really a CD.  It doesnt like dressing in drag and forcing it will probably make it run away.  I have to convince it.

MrBoojive, Thank you for this!  I am booting the Acer right now to see if I can get it to work this way.  I'm sure it'll be just fine.  I'll go ahead and ask this preemptivly, and will have hopefully figured it out by the time this is read but: Are he DEBs named such that I'd be able to recognise them in the Pool folder?

-David

---

### Post by psychlopath on 2009-11-12
Interesting: When I try to install B43-fwcutter (which is what I think I need for my wireless...almost sure it's what I installed back when I actually had everything working) it freezes, just like when I have "Hardware Drivers," try to install it.  I wonder what's up with that??

---

### Post by mrboojive on 2009-11-13
Maybe try installing bcmwl-kernel-source, instead. That has Broadcom's official Linux driver in it.

---

### Post by psychlopath on 2009-11-13
I got it after a fresh (re-re-re-re) install of NBR.  

I really have no clue why it magically works NOW instead of the first time..or the 3rd time..or the 9th time...

Either way...why question it??

---

### Post by ukripper on 2009-11-13
> **psychlopath said:**
> I got it after a fresh (re-re-re-re) install of NBR.  

I really have no clue why it magically works NOW instead of the first time..or the 3rd time..or the 9th time...

Either way...why question it??

Strange!

---

