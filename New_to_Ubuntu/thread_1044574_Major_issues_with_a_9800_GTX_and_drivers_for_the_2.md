---
title: "Major issues with a 9800 GTX and drivers for the 2.6.27-9-generic kernel"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Ereon on 2009-01-19
Howdy all. I'm a new user of Ubuntu, struggling with getting graphics card support for my Nvidia 9800 GTX graphics card on Ubuntu 8.10 (also known as Intrepid I believe). When I first installed Ubuntu everything was peachy. I download the 180.22 drivers from the linux Nvidia website, and used a guide for manually installing the driver since the 177 and 173 glx drivers the OS suggested did absolutely nothing. It worked for a while, but then I believe I did a major update of some kind, I'm not sure what all changed and I have no idea how to find out what was installed.

Long story short, the driver keeps crashing repeatedly, so I have to revert to generic mode for graphics. I keep trying to reinstall, and flipping between the three different kernels that are on my system (I think I have 2.2.6.27-9-generic, 2.6.27-11-generic, and one slightly lower version) to see if that helps, but I only get the same responses. I even tried downloading the source for 2.6.28.1 and compiling it myself. I managed to install it, but for some reason my monitor won't handle whatever resolution it loads at start up (it only goes up to 1280 x 1024), so I can't do anything with it to see if my card behaves under that kernel. 

The only clues I have as it what might be wrong are that whenever I try to install my Nvidia drivers it's unable to find a kernel module for my kernel (I'm assuming that this is what ties the driver in to the OS kernel) and it has to create one to cope. Also, whenever the installer is checking files it's unable to find one called "libglx.so.xserver-xorg-core" that's supposed to be in the directory "usr/lib/nvidia". Whenever I run through the install I let the installer auto-config a .conf file, and then restart the GDM, but all I get is an error that says "Failed to load module "type1"" and then a message that says "Failed to initialize NVIDIA kernel module" with a krapload of other error messages. Then the display crashes, and I have to revert to default drivers...again...and again...and again. I'm inches away from grabbing any random explosives I can get my hands on and igniting them inside my computer's case. I've pawed and shuffled through pages and pages of google results and nothing has been able to help, so I've finally broken down. Is there anyone who can help?

---

### Post by Ereon on 2009-01-19
Coincidentally, I've found out that the driver I was trying to install was apparantly for Linux kernel 2.6.28, which I haven't been able to get to run. Is there any way to get a 180 driver (or another driver equivalent to 180.22) for 2.6.27-9?

---

### Post by Ereon on 2009-01-19
Would it perhaps be productive to entirely reinstall Ubuntu from scratch and then rework the drivers? I'm considering doing just that, because it seemed to work before.

---

### Post by phen0m on 2009-02-14
Edit: I just updated my kernel to -11 and ran into issues.  The steps outlined here [http://ubuntuforums.org/showthread.php?t=773122&page=4](http://ubuntuforums.org/showthread.php?t=773122&page=4) helped me out.

---

