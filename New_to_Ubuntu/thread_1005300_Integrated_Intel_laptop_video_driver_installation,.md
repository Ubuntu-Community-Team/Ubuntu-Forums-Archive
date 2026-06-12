---
title: "Integrated Intel laptop video driver installation, HELP!"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by crimsonlung on 2008-12-08
Hello everyone!

I have just installed ubuntu for the first time,, I have the newest version, downloaded today.  Everything seemed to go smoothly, except for one thing,  I couldnt get ZSNES to work....
going 
The main reason I installed this OS is because I heard zsnes works on it, it was like, the deal breaker.

I installed it by going to application > add/remove

After its installed, I goto applications > games > ZSNES

When I click it, nothing happens, not even a screen popping up, absolutely nothing happens.  

Me being Windows minded, I assume that this is a video driver problem or a mis directory problem.

Well, I opened up the chess game that came with ubuntu, and I checked the option to change it to 3d mode, and it said "no python opengl support" and "no python GTKGLExt support."

Soooo, because of these 2 issues, I beleive its a driver problem and Ive scoured around the forums and google for many hours trying to find a resolution.

I have found help for nvidia and ati cards but not intel integrated.

Here is my information according to the console:

 *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

My Laptop Specs:

Intel Celeron 575
2.6 ghz 1mb l2cache
up to 732MB mobile intel graphic media accelerator 4500m
2gb DDR2 RAM

Anything you can do for me will be much appreciated, thank you so much.

---

### Post by DaveyG on 2008-12-08
Hi crimsonlung, Welcome to Ubuntu Forums :)

First things first...

Which Version of Ubuntu are you using? Also try checking if you have any Drivers enabled/installed. Check at System -> Administration -> Hardware Drivers, select the required (if any listed)

Hopefully that might solve your Problem

---

### Post by crimsonlung on 2008-12-08
> **DaveyG said:**
> Hi crimsonlung, Welcome to Ubuntu Forums :)

First things first...

Which Version of Ubuntu are you using? Also try checking if you have any Drivers enabled/installed. Check at System -> Administration -> Hardware Drivers, select the required (if any listed)

Hopefully that might solve your Problem

Hi Davey, thank you for the welcoming.

Well, I have Ubuntu 8.10 which was the newest one as of yesterday, I go to the hardware section and I have 0 proprietary drivers in use on this system.  I would like to install them, but I have a laptop, which isnt custom built like my PC is.  Is this request even possible?  Where would I begin?

I am sorry for being so newbish, I am pro with Windows....

---

### Post by reacocard on 2008-12-08
intel graphics should work out of the box. The chess game issue is not related to drivers (its a missing dependency). Please try running zsnes from a terminal (Applications->Accessories->Terminal, type in 'zsnes' and press enter), and post any output it gives here.

---

### Post by crimsonlung on 2008-12-09
> **reacocard said:**
> intel graphics should work out of the box. The chess game issue is not related to drivers (its a missing dependency). Please try running zsnes from a terminal (Applications->Accessories->Terminal, type in 'zsnes' and press enter), and post any output it gives here.

Hello, I tried what you did and I got farther then before, however, still nothing happened.  I got something to show up in the terminal:

"
crimsonlung@ubuntu:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

-----------------------------------------------------------

Starting Mouse detection.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated

Aborted
"

--------------------------------------------------------------------------

So i thought it was aborting because of it not recognizing my mouse so I plugged in my usb mouse, still nothing.


EDIT:

OK, sooo,  I tried running "sudo zsnes" and I got this instead:

"
Starting Mouse detection.
ManyMouse: 4 mice detected.
Using ManyMouse for:
Mouse 0: Logitech USB Optical Mouse
Mouse 1: AlpsPS/2 ALPS GlidePoint
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d1b558]
/lib/tls/i686/cmov/libc.so.6[0xb7d19680]
zsnes[0x8056c1b]
"

any ideas or thoughts?

what is a buffer overflow?

---

### Post by crimsonlung on 2008-12-09
> **reacocard said:**
> intel graphics should work out of the box. The chess game issue is not related to drivers (its a missing dependency). Please try running zsnes from a terminal (Applications->Accessories->Terminal, type in 'zsnes' and press enter), and post any output it gives here.

also, when you say it should run out of the box, why doesnt it show up in the driver hardware list?

---

### Post by igknighted on 2008-12-09
> **crimsonlung said:**
> also, when you say it should run out of the box, why doesnt it show up in the driver hardware list?

That list is only for drivers that cannot be shipped with ubuntu due to license restrictions (nvidia, ati, many wifi, etc.).  Intel provides open source drivers for its graphics cards, and thus can be distributed with the distribution.

EDIT: Do you have desktop effects working (ie fading, wobbly windows, cube, etc.)?

---

### Post by zombiepig on 2008-12-09
> **crimsonlung said:**
> also, when you say it should run out of the box, why doesnt it show up in the driver hardware list?

The driver hardware list is only for things ubuntu is NOT allowed to ship out of the box. There's certain drivers that ubuntu can't legally include, so it leaves it up to users who need these drivers to manually install them. 

Because your intel graphics card is fully supported by a standard ubuntu install, you don't need to install anything from hardware drivers to get it functioning.

---

### Post by crimsonlung on 2008-12-09
> Do you have desktop effects working (ie fading, wobbly windows, cube, etc.)?
[/QUOTE]

Hmm, I am not quite sure what this is, where can I check on this?

---

### Post by Tatty on 2008-12-09
System->Preferences->Appearance->Visual Effects

---

