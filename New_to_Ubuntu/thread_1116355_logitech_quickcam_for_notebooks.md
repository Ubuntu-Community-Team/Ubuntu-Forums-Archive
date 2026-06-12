---
title: "logitech quickcam for notebooks"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by DarinB on 2009-04-04
i just got this logitech quickcam for notebooks i saw on the ubuntu hardware list it is out of the box. no what i installed gspca but i am stuck.

---

### Post by billgoldberg on 2009-04-04
> **DarinB said:**
> i just got this logitech quickcam for notebooks i saw on the ubuntu hardware list it is out of the box. no what i installed gspca but i am stuck.

Out of the box means it will just work, you don't need to do anything.

Fire up "cheese" and see if it works.

---

### Post by DarinB on 2009-04-04
i know but it doesn't do anything

---

### Post by DarinB on 2009-04-04
does anybody have a clue how to get this working i saw the logitech quick cam on the hardware list is say out of box but i am not getting anything any ideas i do see it on lsusb
Bus 002 Device 004: ID 03f0:4e11 Hewlett-Packard Photosmart 2570 series
Bus 002 Device 002: ID 05e3:0716 Genesys Logic, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:08dd Logitech, Inc. QuickCam for Notebooks
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
darin@darin-desktop:~$

---

### Post by Sef on 2009-04-04
Do you have another computer to try it on?  The problem could be with the camera too.

---

### Post by DarinB on 2009-04-05
yes it worked at the store he tried it

---

### Post by nandemonai on 2009-04-05
> **DarinB said:**
> does anybody have a clue how to get this working i saw the logitech quick cam on the hardware list is say out of box but i am not getting anything any ideas i do see it on lsusb
Bus 002 Device 004: ID 03f0:4e11 Hewlett-Packard Photosmart 2570 series
Bus 002 Device 002: ID 05e3:0716 Genesys Logic, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:08dd Logitech, Inc. QuickCam for Notebooks
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
darin@darin-desktop:~$

Mine works on 8.10 completely updated.

Bus 005 Device 002: ID 046d:08dd Logitech, Inc. QuickCam for Notebooks

For a time it didn't and I tried compiling a driver for it here:
[http://forums.quickcamteam.net/showthread.php?tid=22&page=1](http://forums.quickcamteam.net/showthread.php?tid=22&page=1)

Though as of Intrepid that driver no longer compiles.

It always worked on Intrepid for skype but nothing else would pick it up. Weird though, I just booted up cheese and viola it seems to be working.

Not sure what to tell ya.

If by chance you're on Hardy then that link above will help you out.

---

