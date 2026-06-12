---
title: "I cannot play any sound."
date: 2009-09-09
forum: New to Ubuntu
---

### Post by paulmmj on 2009-09-09
Hello Ubuntu Forums,

I switched over from Windows XP two days ago, and I am enjoying every minute of it. Single booted the drive, for after a brief demo of Ubuntu I was convinced. But ya know, as always with these things, I've had a few little issues. Most are now sorted out, but no matter what I do, I can't get sound to work. I've tried re-installing what I believe to be the correct drivers, I've tried all the drivers in the sound preferences menu, I've made sure it isn't on mute, and that my speakers work, but I just can't get it to play anything through my computer. But I can get it to beep loudly if I hit "Test" in sound options. I believe I have a SoundBlaster MAX Audigy 2, or something to that affect. I'm not computer illiterate, but I'm also no computer scientist, so could I get some advice, please?

Thanks,
Paul.

---

### Post by Perfect Storm on 2009-09-09
Have you disabled the onboard sound card in BIOS if your motherboard have one? It may mess things up.

---

### Post by vgrisham on 2009-09-09
Hi Paul,

Right click on your volume icon in the system tray and choose Open Volume Control. Make sure that all of your switches are turned up. For example, my laptop has a headphone jack with a separate volume control than master. Tinker with those and see if that doesn't fix it.

Vaughn

---

### Post by chkneater on 2009-09-09
Some advice from someone that hates sound issues, don't try to install or uninstall any drivers unless you absolutely know what drivers you are dealing with, someone from ubuntu.org or launchpad.net advises you to, or synaptic tells you that it has to in order to do something.  The reason why is a lot of the drivers have a dependency on some other file, or in some cases a file will have a dependency on the driver.  Either way, anything that deals with your driver has to be told that the driver has changed and what driver it changed to.  Arbitrarily changing drivers will lead to DOOOOOM!  Not really.  First thing check your speaker icon is not at mute or zero, check speakers or ON and connected to the right port.  
Next first thing, reboot your computer and watch the startup screen.  Look for anything that seems abnormal especially with audio, you won't catch everything but it's not important.  Just keep your eyes open, this will help you get to know your computer as well as looking for errors.  When the screen says something along the lines of "Press" F10 or del or something " to enter system BIOS" or "to enter setup", DO IT.
Once in the BIOS look for system speaker and turn it off, save, exit.  SYstem speaker is the stupid one toned speaker that beeps at you when you fall asleep with your forehead on the keyboard and type an endless number of Q's.
 
Next open a terminal and type

alsamixer

This will bring up the levels of device that uses your sound card.  PCM is the primary and all the subsequent channels go through this one.  It also sets the default system value.  Some things need to be muted, but you can "prediagnose" your problem by playing and audio file and muting then unmuting channels or vice versa.  Just make sure you leave everything the way you found it.  All of this needs to be checked b4 you ever mess with drivers.

---

### Post by Mission 10 on 2009-09-09
Disabling from bios usually does the trick. Use asondconf to make sure only one card is seen to make sure that it's disabled.
```
asoundconf list
```

---

### Post by paulmmj on 2009-09-09
Thank you very much, everyone!

I'll proceed to disabling this "motherboard speaker", and I am certain it is this because my "motherboard speaker" has been incessantly annoying in that it makes a wide variety of different noises when I do something it disapproves of. If my sound was working, this post would've probably been along the lines of, "how do I get rid of the annoying system sounds coming from inside my computer."

Thanks,
Paul.

P.S. - You put "Microsoft Customer Care" (an oxymoron...) to shame. I called them up for when I had this same problem in Windows XP and they told me it was a driver issue and to find the right driver. "Finding the right driver" took 3 days or Googling...

---

### Post by paulmmj on 2009-09-09
It works! Yes! Thank you! I am so pleased!

I will not miss the long waiting lines, then the "ellomynameisBobandhowmayIbeofhelpingyoutoday?" in broken English, and then even after that, not fixing anything.

---

### Post by vgrisham on 2009-09-09
My favorite part of those phone calls is when they put you on hold and you *know* they're Googling for a solution.

---

### Post by paulmmj on 2009-09-09
hahaha. I never thought of that, but you are undoubtedly correct. But Apple's Customer Care is surprisingly helpful, in true Steve Jobs fashion.

---

### Post by vgrisham on 2009-09-09
> **paulmmj said:**
> hahaha. I never thought of that, but you are undoubtedly correct. But Apple's Customer Care is surprisingly helpful, in true Steve Jobs fashion.

Yeah, but their hardware is crap. Our business runs Mac based software (alas, where are the Linux salon management packages?). We have two macbooks and an iMac. All three have suffered hard drive failures within the first year. Both macbooks had motherboard issues and had to be sent in for service in their first six months of service. You'd better have good service when your equipment is as flaky as Apple's is becoming.

Edit: I have to add that when our iMac died, the Apple service rep actually told us that we must have used it too much. I guess they design them now to just sit there and look cool.

---

