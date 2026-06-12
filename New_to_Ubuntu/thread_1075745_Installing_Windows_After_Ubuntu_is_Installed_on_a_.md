---
title: "Installing Windows After Ubuntu is Installed on a Seperate Partition"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by WillieMaysHayes on 2009-02-20
Hi Ubuntu Forums,
I've recently built a PC that I have installed Ubuntu 8.10 64-bit on.  I really like Ubuntu, but I would like to put Windows 7 on another partition.  I've used gparted and I've successfully shrunk the Ubuntu partition and I reformatted the empty space with a new ntfs partition.

Now here's the problem.  I place my Windows 7 DVD in the drive and fire up the PC.  I start to boot from the CD and then GRUB takes over and boots up Ubuntu.  The Windows boot never gets past the "Press any key to install...".

I've got several ideas on how I could deal with this, but I'm not sure of the right way to go about this.  Does anyone have any helpful suggestions?  It would be much, much appreciated.

I'm assuming that I probably just need to tell GRUB the other partition is there but I am not confident and I'm too new to Linux to guess.

Thanks in advance,
Josh

---

### Post by JohnLM_the_Ghost on 2009-02-20
Hmm make sure BIOS is booting CD first!
Also you should know that Windows installation will overwrite MBR (thing what tells to run GRUB on boot), but it can be restored with a bunch of commands from terminal... Keep a Ubuntu LiveCD close by.

Oh and yes... Welcome to Ubuntu forums! ;)

---

### Post by Therion on 2009-02-20
How to Dual Boot Linux and Windows XP (Linux Installed First):

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by WillieMaysHayes on 2009-02-21
Thanks John and Therion.  Good info from the both of you.

I was able to figure out the issue and let me tell you that the root cause is quite stupid!  I noticed that when the Windoze 7 installer asks me to press any key that the PC seems to not respond perhaps?  I have a Logitech S520 USB Wireless keyboard.  I immediately recalled the lesson I learned with an old version of gparted the other day.  Older versions of gparted do not support USB!  So I went and dug out a PS/2 keyboard (can't believe I still had it...) and restarted the PC.  When I went to press the "any" key (still searching for that "any" key...its not on my keyboard...) the Windoze 7 installer then popped up.

Just as John had said, GRUB was toasted.  So time to go put it back.  Thanks again for your help.  :D

---

