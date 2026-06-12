---
title: "Boot script in 8.04, where to find it?"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by L a r r y on 2009-07-30
This computer has had some long waits in the boot sequence, and I am  still very green on where and how Ubuntu boot scripts are run.

If someone can point me the direction, I will follow out the links to the information.

I will come to my boot menu (Grub), start Ubuntu and see a few lines of code on the screen, then go into the Ubuntu splash.  During the splash, there is one pass back-and-forth while searching, then the "thermometer" starts growing.  Fully grown, I switch to a blank screen and wait about a minute before the desktop background comes up, then the log-in screen appears.

Following the accidental erasure of a hard drive with GParted, there are now two missing mounted partitions that cause a Bash screen to come up after the splash and before the black screen event.  I have to intervene and hit CTRL-D to close the Bash screen and continue booting.
-----
I recently used gparted to create a new partition in some unallocated space on my secondary hard drive, and wanted to give that partition a volume label.  I used disk label, a big mistake.  It wiped the hard drive clean, leaving me with one big unallocated space.  Fortunately Windows and Ubuntu are hosted on a different drive!

(Any ideas on recovery of this blown disk drive?)
-----
About the black screen delay:  I had to edit the Xorg configuration to force it to display something besides 1200x1600 or 640x480 and at most 800x600, when I am shooting for 1024x768.  But there is still apparently something that was never configured right, and the computer hangs for awhile trying to find whatever it won't find.




I am running a K7S5A mainboard with a 1 GHz AMD Athlon processor, 512M of memory, onboard video, and onboard NIC, and a Diamond Multimedia sound card.  The onboard sound is disabled, after I plugged a microphone into the front panel speaker jack -- Two poorly-labeled jacks on the case front and I chose the wrong one and blew the right channel output long before I introduced Linux.

---

### Post by Humanum on 2009-07-31
Hi,


Why don't you try to run recovery mode and see all the details... and then if nothing pop up, you can try to use the command line and type > startx...

---

