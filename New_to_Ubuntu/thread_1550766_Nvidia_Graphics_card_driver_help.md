---
title: "Nvidia Graphics card driver help"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by shock72 on 2010-08-11
I just installed Ubuntu 8.04 yesterday and while I have used it a few times in the past on a dual boot system I'm not very experienced with linux. 

I'm running an athlon xp 2600+ with 2 gb of ram and a newly installed Nvidia geForce 9400 gt pci card (regular pci not pci-e) with 1gb vram. When i installed ubuntu it didnt detect the card so i started looking through various forums and websites to figure out how to get it installed. 

I spent all day yesterday frustrated and trying to get the card installed and still havent gotten anywhere. before anyone asks, Yes the bios is set to PCI and not the AGP card. 

the system hardware driver list says "no proprietary drivers are in use on this system"

so heres a rundown of what i did. 

-downloaded the Nvidia driver from Nvidia site, the driver for my card is  "NVIDIA-Linux-x86-256.44.run"

-purged all nvidia drivers that may be loaded on the system with the command sudo apt-get --purge remove nvidia-*

-installed the driver from the console and got this "ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differsfrom the one used to build the target kernel, or if a driver such asrivafb/nvidiafb is present and prevents the NVIDIA kernel module fromobtaining ownership of the NVIDIA graphics device(s)."

- blacklisted files in modprobe.d
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

- purged all nvidia drivers and installed the driver again 

This time I got a Kernel Source tree error. 

-updated all of the headers and kernel source
-purged nvidia again and tried to reinstall

finally got it installed 
"
> Kernel module compilation complete.
-> Installing both new and classic TLS OpenGL libraries.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (256.44):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq 2.6.24-28-generic'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: Y
   es)
-> Your X configuration file has been successfully updated.  Installation of
   the NVIDIA Accelerated Graphics Driver for Linux-x86 (version: 256.44) is now complete.

-reboot and i get a message age asking if I want to configure the driver and I get a box that says "you are running in low graphics mode" and the option to configure the video card. 

when i hit configure it shows the current driver and then i can select a specific card from a list, if I go down the list the highest cards listed are the geforce 8 series.  If I select use current driver and hit test the screen goes black and I have a giant square for a mouse cursor. 

I have the nvidia xserver setting listed under preferences but when i open it i get "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." I restarted x and went back to the nvidia settings and it just gives me the same error message. 

so thats where i'm at now. How do I get this card working ? I have never had so many issues trying to install a video card. I even tried doing an upgrade to ubuntu 10.04 and still had the same problem.

---

### Post by sikander3786 on 2010-08-11
Hi.

A basic question at first. Why did you install 8.04? Any special reason behind it? 10.04 is out and it is as well an LTS release. Why don't you give 10.04 a try?

---

### Post by shock72 on 2010-08-11
well because i just happened to have a disk with 8.04 on it and i have used that version before. 

I finally gave up with the nvidia card and decided to throw the old ati 9550 agp card in and it works fine. The only issue I may have is that I play WoW and that was pretty much the whole reason I wouldnt switch over to linux but I decided i'm going to try and install it and run under wine but I'm not sure how my FPS will be with this old 256mb card

---

### Post by JBAlaska on 2010-08-11
I think you'll find ATI cards don't work nearly as well as Nvidia in Linux.

I'm not sure exactly why your having problems, as the geForce 9400 gt should work fine with Ubuntu.

I have the 9500 GS working perfect with the proprietary drivers on 10.04.

You really should try using Ubuntu 10.04 before you give up on the Nvidia card.

---

### Post by shock72 on 2010-08-11
I tried 10.04 with the Nvidia card with the same result. I'm upgrading to 10.04 again and i may give it another shot but after 12+hrs of screwing with this card I'm about over it.

---

