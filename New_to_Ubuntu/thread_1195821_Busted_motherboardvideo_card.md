---
title: "Busted motherboard/video card"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by andy_blah on 2009-06-24
I just got up from my comuter to get something from the other room, came back, moved the mouse a bit and the monitor went on stand-by mode. After this I tought that the video card might be acting up or it might have been overheated, so I turned off the PC and started it again, only to find out that the monitor was still on stand-by after starting the PC, and it started making one long beep followed by two shorter ones(I have a Phoneix AWARD BIOS), looked up for that beep sequence over the internet and in one place I found out that "It indicates a video error has occurred and the BIOS cannot initialize the video screen to display any additional information" or "Video failure". After that tried to remove the video card to see if it makes any difference, unfortunately it didn't. Earlier today I hard a small explosion bu I'm not sure of the source of that sound because I was listening to some music at the time, but it seemed that it was somewhere close to me; still I can't be too sure if it was from the PC, also checked inside and nothing seemed to have exploded. Please note that I heard the sound 3 hours before the monitor incident happened :P. I was going to take it to the nearest computer repair shop tommorow, but before that, can anybody suggest me to try anything else (besides trying with another video card because I don't have one and I don't really know anybody who has an AGP x4 video card ^_^; ).

If it helps the motherboard of the PC is MSI's P4MAM2-V with a Intel Celeron D CPU at 2.26GHz, 384MB RAM and a NVidia GeForce 5500FX video card.

And if this issue was posted in the wrong thread, I ask the moderators to move it in the appropiate forum. I posted it here because I am an Absolute Beginner when it comes to hardware :P

---

### Post by overdrank on 2009-06-24
> **andy_blah said:**
> 

If it helps the motherboard of the PC is MSI's P4MAM2-V with a Intel Celeron D CPU at 2.26GHz, 384MB RAM and a NVidia GeForce 5500FX video card.

And if this issue was posted in the wrong thread, I ask the moderators to move it in the appropiate forum. I posted it here because I am an Absolute Beginner when it comes to hardware :P

It appears that model motherboard has onboard video  	S3 Graphics ProSavage8
Have you tried connecting to it?

---

### Post by wpshooter on 2009-06-24
Make a WIN98SE bootable diskette and see if the computer will boot to that diskette.  Make sure diskette drive is first bootable device in BIOS.

If it will boot to it and you can get the text screen displays of the WIN98 operating system then it is not very likely that your video card is bad.

When you start talking about poping or explosions the first thing that comes to my mind is possible problem with computer power supply and perhaps it has destroyed something in the video section of the motherboard.

P.S. - Are you getting any video at all, can you see initial boot screen and can you get into an view BIOS screens ?

---

### Post by andy_blah on 2009-06-24
> **overdrank said:**
> It appears that model motherboard has onboard video  	S3 Graphics ProSavage8
Have you tried connecting to it?

If by "connecting to it" you mean to switch to it, then it is imposible to do that because the monitor doesn't display anything when I start the PC :(, as I said in my initial post: 

> **wpshooter said:**
> P.S. - Are you getting any video at all, can you see initial boot screen and can you get into an view BIOS screens ?

Unfortunately, no, I can't see anything, the monitor is on stand-by even 30 seconds after starting the PC, so I can't try what you suggested :(

> **wpshooter said:**
> When you start talking about poping or explosions the first thing that comes to my mind is possible problem with computer power supply and perhaps it has destroyed something in the video section of the motherboard.

At that moment when that sound occured, I haven't sen anything unusual or smelled somethng burnt or anything like that which puzzles me ~.~;

---

### Post by jmfal on 2009-06-24
re:andy_blah
There are a couple of things to check out. If you have another pc try hooking your monitor to it ,to see if it is ok.
If its good, open up your pc and check the capacitators, look to see that none are split down the side,or bulging tops. If there is mobo is shot.
From what i know, if you clear the cmos, that will reset your bios to factory settings. Plug your monitor into mobo video,you have to remove your agp card!!
you may very well have p/s problem, so if you think you might do more damage replace it first. power suppies have bad habit of frying other components when they go out.
sorry about misfortunes hope you get running without to much trouble

---

### Post by andy_blah on 2009-06-24
> **jmfal said:**
> 
There are a couple of things to check out. If you have another pc try hooking your monitor to it ,to see if it is ok.

Yes, the monitor works fine, and I already knew that it is :P 

> **jmfal said:**
> If its good, open up your pc and check the capacitators, look to see that none are split down the side,or bulging tops. If there is mobo is shot.

I have two of those capacitors bulged a little, but from what I can remember, they always were like that

> **jmfal said:**
> From what i know, if you clear the cmos

And how can I do that? If it is graphically, forget it :P

---

### Post by starcannon on 2009-06-24
As stated clear cmos, directions will be in the documentation area for your motherboard at the MSI website.

Bulging Capacitors is NOT good; if they are popped then its over.

Moving on as though the Capacitors are still functional; be sure after clearing cmos, to go into the bios setup, set to optimized defaults, then, turn OFF the onboard video, set agp to the first display device, save, and exit.

Let us know how it works out after that.

GL

---

### Post by andy_blah on 2009-06-27
Sorry for my late reply, I had some other problems to solve besides this one ^_^;

I looked on MSI's site, and it told be to refer to my motherboard's manua, I did, and I found this:

"You can clear CMOS by shorting 2-3 pin while the system is off. Then return to 1-2 pin position" (the pins are actually shown on the motherboard's map)

This is what puzzles me because it doesn't say if I have to start the PC or not. So, after moving the cap on 2-3 pins, do I have to start the PC, turn it off, after that to move the cap back on 1-2, or just move the cap on 2-3 and immediately after, move back to 1-2(without starting the PC)?

And since I know that the video card doesn't seem to work, I will have to try the onboard one, if that doesn't work, I will probably not be able to access the BIOS :P

---

### Post by QIII on 2009-06-27
Yeah.  It seems the instructions might not have been clear.  First, I would try without powering back up.  Just leave the jumper there for a bit, get a cup of coffee and reset the jumper to its original position before restarting.

In the old days, I seem to remember changing the jumper, powering up and powering back down after some sort of warning from the BIOS that you were doing what you were doing.

Be aware, however, that you will probably be setting your BIOS back to its original settings and you will have to re-do any changes you have made.

---

### Post by andy_blah on 2009-06-27
Did what QIII hs suggested and it works! Could have accessed the BIOS afterwards, loaded the optimized settings and changed a few around so I could use my PCI soundcard, didn't set the AGP video card as default yet because I want to take the PC to the repair shop first to see exactly what's the problem, and still I suspect that the video card isn't the problem here. 
Booted on Ubuntu, and it seems that the onboard video works properly. That you all for your help on making my PC at least functional :P

---

