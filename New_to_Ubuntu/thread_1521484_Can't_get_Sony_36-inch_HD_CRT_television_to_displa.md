---
title: "Can't get Sony 36-inch HD CRT television to display signal via component inputs"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by Gainesvillian on 2010-06-30
I recently purchased a new computer with Ubuntu 10.04 installed from a local computer store.  My plan is to use it with my Sony KV-36XBR4OO television, a 36-inch CRT model from 2001 that has component (Y,Pb,Pr) video inputs for high definition picture.  (The store knew this in advance.)

Motherboard: MSI G31TM-P21 LGA 775 Intel G31 Micro ATX
Processor:  Celeron 430, 1.8GHz, 800MHz FSB, 512KB L2 Cache, 65nm, 35W, EM64T EIST XD
Memory:  SuperTelent 2GB PC2-6400 DDR2 800 MHz
Video Card:  Asus nVidia GeForce EN8400GS Silent 512MB DDR2 VGA/DVI PCI-Express 2.0

When I first booted up the computer, attached to my TV with the TV on, I got only a very distorted signal that was almost impossible to read.  (The connection is using a long VGA-to-component adapter cable.)  Then, adding an old Dell LCD computer monitor via the video card's DVI output, I was able to see a clear picture on that monitor, but was unable to adjust the settings to get a clear picture on the Sony TV.  (I was using the System > Preferences > Monitors tool.)

So, then, using System > Administration > Hardware Drivers tool, and downloading the nVidia accelerated graphics driver (version 173), I tried again.  After rebooting I got no signal to the Sony TV at all.  The Dell still works fine.)

So, then I downloaded the other driver that was available from the same method, which said it was "current" and "recommended."  Still, no dice.  After rebooting there was no signal to the Sony TV.

Going to System > Preferences > Monitors (or System > Administration > NVIDIA X Server Settings, same thing) shows:

CRT-0 - (Dell E153FP)
CRT-1 - (CRT-1)

Clicking on the Dell monitor to select it brings up a configuration area on the right side of the window to change the Digital Vibrance or the Overscan Compensation using sliders.  Refresh rate is given as 60.00 HZ.

Selecting CRT-1, however, only brings up the message "Refresh Rate: Unknown."  There is nothing to adjust to get a picture on the Sony TV.

The computer shop owner is not too familiar with Ubuntu, and his only suggestions have been to switch to Windows, or try a TV tuner card.  I really would like to use Ubuntu if possible, but am not too familiar with it myself.  Is there any way to get this system working with my old Sony TV?  Would a different video card work better?  Or will I have to switch to Windows, or replace my television?

Any advice or solutions would be much appreciated.           :confused:

---

