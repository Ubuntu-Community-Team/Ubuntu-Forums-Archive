---
title: "Sapphire Radeon x1050 ATI drivers help"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by SandShark on 2011-01-18
Hello to all :)
Since I'm absolute beginner, I ask you to have patience with this one
I have just installed ubuntu 10.04 on my PC (on boot I can choose between WinXP or Ubuntu - I think that's dual boot???)and am still on 800x600 resolution. I ask you for some help installing the drivers for my x1050, because on the previous Ubuntu I installed there were many things I didn't understand how to install and finally - got all wrong :-( 
I'm running Ubuntu on 512 mb RAM , Intel Celeron 2GHz and of course - Sapphire X1050

Regards - SandShark :)

---

### Post by smurphy_it on 2011-01-18
Have you tried going to ATI/AMD's website and downloading the driver for linux ?

Linux x86 or x86_64 = [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

---

### Post by SandShark on 2011-01-18
X86
How do I install it anyways, I have to use terminal, but am not sure which package should I install (there are many packages when I run the --listpkg in terminal).

---

### Post by smurphy_it on 2011-01-18
If it's anything like I'd done in the past.  It will download one file (a .run file).  You would install that in your terminal.

Then open a terminal, navigate to where you downloaded the .run file and type the following:

sh ati-driver-installer-9-3-x86.x86_64.run

Follow the prompts and off to the races you go.

---

### Post by mastablasta on 2011-01-18
> **smurphy_it said:**
> If it's anything like I'd done in the past. It will download one file (a .run file). You would install that in your terminal.
 
Then open a terminal, navigate to where you downloaded the .run file and type the following:
 
sh ati-driver-installer-9-3-x86.x86_64.run
 
Follow the prompts and off to the races you go.
 
REALLY? Did you check?
 
> AMD has moved a number of DX9 ATI Radeon&#8482; graphics accelerators products to a legacy driver support structure.
See more here: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)
 
Which in short means ATI dropped their linux support for this graphics card and you can only use **OPENSOURCE drivers** with this card from i think Ubuntu 8.04 (or is it 8.10) onwards. Attempting to install proprietary drivers can seriously damage your system!!!! opensoruce drivers are the ones that install by default
 
you should be able to change resolution. X series don't have as good support it seems in opensource drivers, but things should work good enough.

---

### Post by smurphy_it on 2011-01-18
I don't have that specific hardware to check.  I've installed drivers in the past that route.  Usually no problems.  Can't speak for "support being dropped though".

---

### Post by SandShark on 2011-01-18
Oh... now that's just horrible ... Anyways, I don't intend to play games on this one, how can I atleast change my resolution? At System->Preferences->Monitors I only get to use 800x600 and 640x480...

---

### Post by mastablasta on 2011-01-18
yes, but not anymore. also now they can be installed through Hardware drivers menu. ;-)
 
Ah yes just found the info Ubuntu 10.04 runs on X.org 7.5. there is also some other requirements that might not be met with older drivers.
 
Anyway here is some informaiton on X configuration. [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)
 
hopefully someone will come allong with magic commands that will fix the OP's issue :-D

---

### Post by Mark Phelps on 2011-01-18
> **smurphy_it said:**
> I don't have that specific hardware to check.  I've installed drivers in the past that route.  Usually no problems.  Can't speak for "support being dropped though".

Then, you shouldn't be advising folks, especially in this forum where they will tend to do whatever you suggest, to do something that has the potential for hosing up their system!

---

### Post by Mark Phelps on 2011-01-18
There is no "magic" solution here!  As said, more than once already, AMD/ATI has dropped restricted driver support in Linux for this card years ago!

You're not going to be able to get AMD drivers to work in current Ubuntu versions due to conflicts between the drivers and the X-server.  The open source drivers (installed by default during setup) are the ONLY drivers that will work.

---

### Post by SandShark on 2011-01-20
> **Mark Phelps said:**
> There is no "magic" solution here!  As said, more than once already, AMD/ATI has dropped restricted driver support in Linux for this card years ago!

You're not going to be able to get AMD drivers to work in current Ubuntu versions due to conflicts between the drivers and the X-server.  The open source drivers (installed by default during setup) are the ONLY drivers that will work.

Thank you for your time :) I still love Ubuntu and will stick to it ^^

Regards

---

