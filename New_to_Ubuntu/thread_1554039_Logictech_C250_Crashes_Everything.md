---
title: "Logictech C250 Crashes Everything"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by gsabina2 on 2010-08-16
I've been using Ubuntu successfully for about a year, due in great part to the advice and solved bugs posted to this forum, but I know when to admit defeat and ask for help.

I recently purchased a Logitech webcam C250 (product id 046d:0804), which multiple sources pointed to as a linux- (if not necessarily Ubuntu-) compatible camera; I was intending to use it with Skype.  When I first ran it, my entire monitor flashed between blackness and some quickly-vanishing error messaging, then holds steady on a completely black screen.

After verifying that the uvcvideo driver was present, I first attempted the LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so workaround - no joy.  Then I tried installing a gspca driver - no joy.  Then I tried the gstfakevideo workaround - no joy (all the documentation I can find uses qcset, which I don't think is appropriate for my hardware).

I've verified my system requirements meet spec (488 MB of RAM, 1.7 GHz processor) for the camera.

At this point, I was convinced the bug lay within Skype proprietary code.  So I tested with Symphony - same result (black screen requiring reboot).  Then Cheese - same result.  Now I'm just stumped.


Basically, I've crossed out all the fishbones I could think up and I need help.

Running Lucid 10.04 with the 2.6.32-24-generic kernel.  Gnome 2.30.2.  Not sure what video card, but my laptop is a Gateway from 2004, and the only non-factory bit is the hard-drive.


Any help is greatly appreciated.

-Greg

---

### Post by jarviser on 2010-08-16
As you say it's supposed to work on 10.04 (I just ordered one!) so have you tried basic elimination, e.g. does it work on Windoze, does it work on the live CD, does it work on any other distros. Try booting with it plugged-in then selecting the right camera in Skype etc. Does it work with a USB powered hub (USB power shortage).

Are you running Cairo Dock by any chance? in which case try it without (there is a fix for that)

---

### Post by gsabina2 on 2010-08-17
Update for all my fans,

Thanks (jarviser) for the tactical suggestion.  I booted from my 9.10 Live CD to happily discover that the webcam worked on this distribution.  That's the upside.  The downside is that I also tried out - on 10.04 - an old cam I have which produced the same result.

To answer your question: No, am I not using Cairo Dock.

I've partitioned my hard drive now and installed the retro 9.10 to meet my immediate needs, but I am still looking for a more elegant solution - I would like to use 10.04 at some point!

Haven't tried reinstalling 10.04.  Perhaps tomorrow.

---

### Post by jtarin on 2010-08-17
Turn off compiz next time around. I have heard its the culprit in many situations with hardware not working. Nothing workd in Skype. LOL

---

### Post by jarviser on 2010-08-18
Mine arrived. Worked first time in Skype and Cheese. As far as I know, although I am running Mac4Lin, I am not using Compiz.

---

