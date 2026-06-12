---
title: "[SOLVED] Epson Perfection 2480 PHOTO scanner installation problem."
date: 2008-12-07
forum: New to Ubuntu
---

### Post by GrenadierExercise on 2008-12-07
I have recently installed Ubuntu 8.10 desktop amd64 version on my HP Compaq Preario SR1519UK AMD 64 Athlon Desktop as sole system.
All works fine except (there always has to be one fly-in-the-ointment) the system does not seem to find or recognise my scanner, an Epson Perfection 2480 PHOTO.
I have tried with the scanner plugged-in and unplugged (USB) at start up with the same result. XSane image scanner returns the error message "Failed to open device 'snapscan:libusb:003:003'; Invalid argument."
The Sane Project seems to support my scanner with driver "esfw41.bin".
The system recognises other hardware - Epson D92 printer and HP DeskJet 895C printer which both work OK. All other features work fine - email, web browser, speakers and display, with no crashes or unexpected results.
Can anyone help me to get my scanner working please?

---

### Post by shifty_powers on 2008-12-07
according to

[http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

you need

[http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

as the backend to sane to get it working...

---

### Post by GrenadierExercise on 2008-12-08
> **shifty_powers said:**
> according to

[http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

you need

[http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

as the backend to sane to get it working...
Thanks for your pointers to help with my question.
From the references you quote it seems that I need the Sane Backend SnapScan(1.4).
My problem is that I do not know how to install this driver or where it resides, ie somewhere within the downloaded Ubuntu 8.10 system library or elsewhere.
Is there a talk-through anywhere in the system for such an installation?

---

### Post by vgrisham on 2008-12-19
To the original poster, how did you resolve this? I see you've marked the thread as solved. I have the same problem (again) and I can't seem to get this scanner to work in Intrepid.

---

### Post by GrenadierExercise on 2009-01-07
> **vgrisham said:**
> To the original poster, how did you resolve this? I see you've marked the thread as solved. I have the same problem (again) and I can't seem to get this scanner to work in Intrepid.

Sorry my delay in responding to your query.
I solved my problem with my Epson scanner installation by following the very clear advice given by "bwallum" Nov 8th 2008 in "Hardware & Laptops" forum.
For me the major difficulty was finding the critical file "esfw41.bin".  I tracked down a copy by googling the web and once downloaded and installed using "bwallum" advice all seems OK, but still testing the scanner.
PS - I am still getting to grips with "XSane Image Scanner"

---

### Post by vgrisham on 2009-01-07
Okay. Thank you. I'll try to follow that trail.

---

