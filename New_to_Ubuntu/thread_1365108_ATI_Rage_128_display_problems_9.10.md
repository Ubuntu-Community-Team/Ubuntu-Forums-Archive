---
title: "ATI Rage 128 display problems 9.10"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by bgmort on 2009-12-26
I just took the plunge and installed Ubuntu 9.10 (my first linux installation) on an older computer using Wubi.  It is running, but the display is not configured correctly.  I have been searching for a solution, and almost everything i can find is for pre-9.10 versions of Ubuntu.  I can only get resolutions of 800x600 at best, and   the display is garbled with horizontal lines across the screen.  The whole display is also shifted to the right so there is a black area on the left side of the screen, and the right 20 or 30 pixels are off the right side of the screen. It is like this from the moment the computer is powered up, including the screen where I select Ubuntu or windows XP, and stays that way unless i boot using XP.  
I have been unable to add any others using the instructions found at [http://www.competo.com/articles/2009/12/19/custom-display-resolution-in-ubuntu-9-10/](http://www.competo.com/articles/2009/12/19/custom-display-resolution-in-ubuntu-9-10/) or similar instructions.
Here is the relevant output from lspci:
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF

When in XP the resolution is 1152x864.  Display settings offers a long list of other resolutions but none of them work correctly.  I think if i can just add 1152x864 to the list in Ubuntu it should work fine, but I have been unable to add it.

Can anybody help me here?

---

### Post by bgmort on 2009-12-28
note - i was able to get the 1152x864 resolution added to the list, but when i tried to change to that resolution i got a message saying that it was invalid

ideas?

---

### Post by mapes12 on 2009-12-29
> 01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
I had one of those video adapters built into a m/board on another PC and couldn't get the res correct no matter what I tried. After much googling I realised that ATI do not support the device anymore. So I bought a cheap NVIDIA PCI card off eBay. That worked. I don't do PC gaming so my video requirements are modest.

:lolflag:

---

### Post by lavinog on 2009-12-29
You might need to try 1024x768.
1152x864 seems like an odd resolution.

Edit: Some older cards could not support anything higher than 800x600 in 32bit color.  You might have to change the bit depth to 16bit to get higher resolutions.

---

### Post by billiardman on 2010-02-24
Installed KK 9.1 and video is working. I have an VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF and would like to enable the visual effects. I have searched long and hard to figure out the solution, but it seems that I have not found the answer yet.  I HAVE NO XORG.CONF FILE TO EDIT.  I tried to create a file with xserver but no go. I tried installing the Download Center drivers but it caused an error on boot up where I have to click on to use basic display settings to boot. So ended up re-installing to get a normal boot sequence back. Tried using compiz-check but it said there was an error due to multiple display controllers. :confused: How is KK setting the video? What I basically would like to know is what commands are needed to check what settings are being used, where they are and can they be modified and how. I have managed to install on 2 different computers to date, and getting better at figuring things out, but without a settings file to work with, I am stuck. Thanks in advance for any help.:P

---

### Post by lavinog on 2010-02-24
> **billiardman said:**
> Installed KK 9.1 and video is working. I have an VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF and would like to enable the visual effects. I have searched long and hard to figure out the solution, but it seems that I have not found the answer yet.  I HAVE NO XORG.CONF FILE TO EDIT.  I tried to create a file with xserver but no go. I tried installing the Download Center drivers but it caused an error on boot up where I have to click on to use basic display settings to boot. So ended up re-installing to get a normal boot sequence back. Tried using compiz-check but it said there was an error due to multiple display controllers. :confused: How is KK setting the video? What I basically would like to know is what commands are needed to check what settings are being used, where they are and can they be modified and how. I have managed to install on 2 different computers to date, and getting better at figuring things out, but without a settings file to work with, I am stuck. Thanks in advance for any help.:P
Rage 128 does not have enough power for visual effects.

---

