---
title: "Install problem..."
date: 2011-07-03
forum: New to Ubuntu
---

### Post by ubunwhat on 2011-07-03
Ok, I'm having another run at installing Ubuntu on my Toshiba Satellite P205 laptop with the dreaded Intel gma 950 chipset.  After much research I had a brief moment of hope before crashing into dust.  Here is what I have so far...

I have a USB drive loaded and ready to go.  That much is working.

When I boot to the USB in the Toshiba I do get the Ubuntu screen, although it is green lines ( think Space Invaders ) rather than the good old purple.  I am pretty sure that is because Linux really struggles with the 950 chipset and it is displaying in the lowest possible resolution.  Anyway....

I can test memory and all of that happy stuff.  The USB drive works in that regard.

When I first attempted the "Try Ubuntu" option I hit a brick wall.  Black screen.  Left it for over 30 minutes, nothing changed.  Just a black screen.  

So I did some research and found what appeared to be a helpful tip on another thread.  I managed to finagle my way around the menu ( No easy task as the menu itself has clearly changed from when the thread was written ), and was able to edit the last line of the boot menu to "i915.modeset=0 xforcevesa" ( without the quotes, of course ).  This actually seemed to be getting somewhere as Ubuntu started to load in the familiar purple screen and then said "press any key to reboot".  So I pressed a key, it rebooted, and I got... a black screen.  After about 90 seconds of the black screen the machine began to protest loudly by screeching like what sounded like an alarm clock from the speakers.  Aside from the endless digital alarm there was nothing.  Just the black screen.  

Ultimately I would like to be able to install this onto the hard drive of this machine and work through the kinks there, but I need to at least be able to see what is happening.  There's not much chance of working through problems with a black screen.  The drive is formatted to ext4, I don't have or want a Windows partition.  It's Ubuntu or nothing for this machine.  Can anyone offer any advice at all on how to move forward with this?  My guess would be that my next step is to once again boot from the USB, enter the switch to versa, and this time, rather than try Ubuntu simply install to the hard disk while I can.  At least that way I should be able to get a Grub menu when I try to boot.  Does that makes sense?  Or am I way off the mark?

Edited to add another question:  I asked this in another thread but perhaps it bears asking here.  Would it be easier to install the hard drive for this machine in an enclosure and install ubuntu from my current Ubuntu machine?  My concern with doing so is that it will install settings specific to this machine ( Compaq Presario ) rather than the Toshiba Satellite that will be the drive's home should I get this working.

---

### Post by ubunwhat on 2011-07-03
Wow.  61 views and not a single idea?  I must really be screwed here....

---

### Post by Matt__ on 2011-07-03
Whilst not hugely helpful, I have found instances of Ubuntu working on your laptop (google/youtube) and this page saying 9.10 runs well.
[http://www.linlap.com/wiki/toshiba+satellite+p205](http://www.linlap.com/wiki/toshiba+satellite+p205)

What Ubuntu versions have you tried? Maybe 10.04 or even 9.10 might be worth a try? Assuming one of them works you could then start adding whatever functionality you required from 11.04...until it breaks and you find your choke point, or just stick with the earlier version.

Any reason not to use a live cd rather than USB? (I had problems before with certain USB installs that went find from cd)

---

### Post by Rex Bouwense on 2011-07-03
Have you considered an alternate install?  Which version are you trying to install?

---

### Post by wildmanne39 on 2011-07-03
Hi, you can connect the drive to your ubuntu system and install using your system, I did that last week and it worked great, I powered down my system, then unplugged my two hard drives and connected the one I wanted to install it to, then I put the drive back into the other system and it worked great. But, if ubuntu does not like your system then it may not boot when you put it back into the other system. You may have to use nomodeset to get it working.

---

