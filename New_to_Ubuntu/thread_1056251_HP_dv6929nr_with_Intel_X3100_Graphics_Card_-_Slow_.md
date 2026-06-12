---
title: "HP dv6929nr with Intel X3100 Graphics Card - Slow glxgears"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by crjackson on 2009-01-31
Okay - My old laptop LCD screen bit the dust so I purchased the above lappy today and installed 8.10.  Everything works fine out of the box except I noticed that my 3D graphics is slow. glxgears shows 179 fps.

Is there an accelerated driver that can speed this thing up. I CAN live with it but I don't want to.

Any suggestions?

Why didn't I get a lappy with an nVidia or an ATI? Because I got an employee discount and only paid $300. It's got 4GB Ram and a 250GB HD, whith 2.0Ghz intel duel core duo.

Please educate me soon...

---

### Post by crjackson on 2009-01-31
Okay so I'm back to check on this thread. Anyone got an idea?

---

### Post by crjackson on 2009-01-31
Booting to 8.04.2 I find that glxgears is now showing 1180 FPS. Unless someone can point me to a fix for Intrepid I guess I'll be reinstalling everything again.

It's a real shame because my old laptop with 1/4 the memory and an old AMD 64 2.0Ghz CPU puts out 3750 with the ATI 9600 video card.  This one is so much newer, how can it be so much slower?

---

### Post by crjackson on 2009-02-02
Bump

---

### Post by Thelasko on 2009-02-02
Okay, first let me see if I get this straight.  You bought a new laptop with a X3100 graphics card and glxgears gives you 179 fps in Intrepid and 1180 fps in Hardy?

I'm still on Hardy myself, but the Intel drivers have always been a work in progress.  The hardware is okay for Intel cards, but will never be as good as an NVIDIA or ATI.  The latest and greatest drivers for Intel cards should be x[server-xorg-video-intel]("http://packages.ubuntu.com/intrepid/xserver-xorg-video-intel").  There is an ongoing effort to get these cards to perform up to their expectations, and I'm guessing one of these changes broke the driver.

I found a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/315808") on launchpad that seems similar to what you are describing.

> wesley@Grimmjow:~$ glxgears
1805 frames in 5.0 seconds = 360.991 FPS
766 frames in 5.0 seconds = 153.030 FPS
290 frames in 5.0 seconds = 57.912 FPS
355 frames in 5.0 seconds = 70.449 FPS
468 frames in 5.0 seconds = 93.590 FPS
492 frames in 5.0 seconds = 98.239 FPS
523 frames in 5.0 seconds = 104.500 FPS
506 frames in 5.0 seconds = 101.058 FPS
501 frames in 5.0 seconds = 100.043 FPS
411 frames in 5.0 seconds = 82.092 FPS
913 frames in 5.0 seconds = 182.530 FPS
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 21511 requests (19357 known processed) with 0 events remaining.

---

### Post by crjackson on 2009-02-03
> **Thelasko said:**
> Okay, first let me see if I get this straight.  You bought a new laptop with a X3100 graphics card and glxgears gives you 179 fps in Intrepid and 1180 fps in Hardy?

I'm still on Hardy myself, but the Intel drivers have always been a work in progress.  The hardware is okay for Intel cards, but will never be as good as an NVIDIA or ATI.  The latest and greatest drivers for Intel cards should be x[server-xorg-video-intel]("http://packages.ubuntu.com/intrepid/xserver-xorg-video-intel").  There is an ongoing effort to get these cards to perform up to their expectations, and I'm guessing one of these changes broke the driver.

I found a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/315808") on launchpad that seems similar to what you are describing.

Yes that's pretty much it. I can live with Hardy performance, but I really expect this to be at least as fast as my old ati card. I would think that intel would at least try to keep up a little.

The performance drop from Hardy to Intrepid is totally unacceptable. I was hoping someone knew of an easy fix. I reinstalled Hardy and I can live with it but wow...  Is this a drive issue or is the card just so far behind the game no driver will even bring it close to a 5 year old ATI?

---

### Post by crjackson on 2009-02-03
How can I tell what version is already installed?

Have you tried it and what were your results?

Thanks...

---

### Post by Thelasko on 2009-02-03
> **crjackson said:**
> Is this a drive issue or is the card just so far behind the game no driver will even bring it close to a 5 year old ATI?
Most of what I have heard is that it's a driver issue.  From [Wikipedia]("http://en.wikipedia.org/wiki/Intel_GMA#Modern_gaming"):
> Some games and 3D applications will not recognize support for some hardware functionality because of the simplification of parts of these graphics accelerators. The GMA X3x00's unified shader design allows for more complete hardware functionality, but the line still has issues with some games and has significantly limited performance.
> As with recent driver updates, more games have become playable on this hardware.

The cards suck in Windows too, so it's not just a Linux thing.  It seems that Intel is just creating the cards and contractors/3rd party developers come up with the drivers for them.  The cards are typically on the market for some time before decent drivers are released for them.

Years have been spent on the drivers we have now.  Knowing that, I think a 5 year old ATI is a better choice.

P.S. Stay away from the GMA 500!  There are no drivers available for it!

P.P.S. I'm not planning on installing/running Intrepid on my machine.  It's my primary machine and I try not to mess with it (sometimes I can't help myself).

---

### Post by crjackson on 2009-02-03
> **Thelasko said:**
> 
Years have been spent on the drivers we have now.  Knowing that, I think a 5 year old ATI is a better choice.

P.S. Stay away from the GMA 500!  There are no drivers available for it!

P.P.S. I'm not planning on installing/running Intrepid on my machine.  It's my primary machine and I try not to mess with it (sometimes I can't help myself).

Wow, that is sad... Well, I guess I'll just have to be happy that I got the lappy dirt cheap then. It's a very nice unit otherwise. I wouldn't have grabed one with unknown support were it not for the $300 price tag from the retailer.

The LCD went out(mostly) on my old lappy and I jumped at this one due to price, I was just surprised at the poor graphics performance.

Thanks for all the info...

---

### Post by Thelasko on 2009-02-03
One last thing... The Intel X3100 is common in laptops because it apparently uses very little power, and therefore increases battery life.

---

### Post by crjackson on 2009-02-03
> **Thelasko said:**
> One last thing... The Intel X3100 is common in laptops because it apparently uses very little power, and therefore increases battery life.

Gotta admit, it does have great battery life...  Thanks.

---

