---
title: "USB Mouse won't click..."
date: 2010-07-08
forum: New to Ubuntu
---

### Post by Firstpenguin on 2010-07-08
Got my first really usable ubuntu system up and running I've installed distros on old computers before but this is the first one I think I'll be using daily.  I was house sitting and brought along an Asrock Ion330.  Dual core intel atom machine with Nvidid Ion graphics.  set it up got email, IM and a few other things working.  I'm really liking it so far.  I go to set it up somewhere else with a different keyboard mouse and monitor and the input devices aren't working.  I can move the mouse around the screen and that's it.  Keyboard and mouse click seem unresponsive.  

Any thoughts?

---

### Post by Yarui on 2010-07-08
Some other people were talking about this exact same problem earlier today.  One of them said that changing the mouse to a different USB port fixed the problem.

---

### Post by polomint77 on 2010-07-08
Yes, that was me, :)

See this thread - [http://ubuntuforums.org/showthread.php?t=1525335]("http://ubuntuforums.org/showthread.php?t=1525335")

I changed it to a different USB port and it beenn working fine ever since, :)

---

### Post by Firstpenguin on 2010-07-08
Thanks for the advice but that's not the case.  This worked perfectly with an older apple mouse with scroll wheel and 3rd party apple keyboard.  The only wired mouse I have at this new location is a kensington mouse which won't do click one.  It boots up fine and then pops up asking for a keychain password and i can't get beyond that.  The mouse moves around and Docky responds to my mouse.  I can also plug in a usb bluetooth module and see the bluetooth symbol pop up in the top bar.  Responds fine to plugging and unplugging the network cable.  However I can't click anything.  

I tried re plugging the wired mouse a million ways and with or with out different keyboards hooked. 
Not sure the keyboard works either.  What are some keyboard commands I could use to test?
Is there a keyboard or boot option that forces it to link up with a bluetooth mouse?
What is a ubuntu equivalent of a safe boot mode?

Please help.  
RSW

---

### Post by Yarui on 2010-07-08
If you want to test out your keyboard you can try alt-F2, which should bring up a box to run a program from if your keyboard is working.  There should be a safe boot in the grub menu immediately under the option to boot into Ubuntu normally.  If the grub menu doesn't normally show up for you because you boot directly into Ubuntu as a single OS, you can hold shift during the boot sequence to force the grub to display.

---

### Post by Firstpenguin on 2010-07-09
So the keyboard boot commands are working (EDIT) were working, now that shift command doesn't do anything.  I did manage to to get to the boot menu once.  Now I can't.  Once I boot the desktop, I'm back to the same dead end, FRUSTRATING PROBLEM.  Oh and both mac and 3rd party kensington keyboards are unresponsive once it boots straight to the desktop.  Please Help!@  I'd really like this to be my mac alternative for web and personal use.

---

### Post by FTBBoy2115 on 2011-10-11
I'm having this problem as well. I boot up into Ubuntu 11.04 and have mouse click-ability at first, but I loose it shortly thereafter. This morn b4 work, I got an error stating 
 
>  
a malicious client may be eavesdropping on your session ot you may have just clicked a menu or some application just decided to get focus

Right now, I have keyboard control, and I can move my mouse around, I just can't get it to click anything. And no, I highly doubt it's a USB issue that I just need to switch bc I have 2 mouses hooked up, one old fashioned serial and the other is wireless USB. The old fashioned serial is able to wake it from hibernation when the USB keyboard and mouse are not
 
I googled and read many forum threads on the error I got, and they don't work/seem to apply. One post mentioned checking for a keylogger. How would I go about doing that?
Either way, I'm starting to wonder if in my case if it has to do with this ver of Ubuntu being too buggy. Looking at LinuxMint as a more stable alternative :/ Constant crashes, and now this...a bit too agrivatingly unreliable considering my current (limited) experience w linux.

---

### Post by Mark Phelps on 2011-10-12
> **FTBBoy2115 said:**
> The old fashioned serial is able to wake it from hibernation when the USB keyboard and mouse are not

This is a BIOS setting.  Some older BIOS's simply do not allow the PC to be woken from hibernation using USB devices.  If your BIOS does allow this, there will be a setting, probably in the Power section, indicating which devices are enabled.  Make sure the USB devices are enabled.  If they are, and this still doesn't work, you're stuck.

---

