---
title: "Getting a Creative Webcam to work"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by djr80 on 2010-03-07
Hello all.

I've just installed Ubuntu 9.10 and have very been very pleased with it, and found this forum really useful.  I do have a problem however, and that is with my webcam.

It is a Creative VF0220 webcam.  When I run Camorama, the red light comes on with the webcam, but on screen the message comes up "Error - Unable to capture image".  Camorama then closes and the red light goes off.  I can't get any images from it, or the green light on.

I looked up drivers, and these forums recommended me to this website [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
which is where I get lost.

I took a guess and downloaded 
**[gspcav1-20071224.tar.gz]("http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz")**

but I then don't know what I'm doing.  I pressed extract and that seemed to do something.  I then tried to run gspca_build as the readme suggested to do so.  But all this other business about "kernels" etc has left me going mad!

Can anybody help?  Perhaps someone has a similar issue?

Many thanks in advance!

---

### Post by no2498 on 2010-03-08
try your cam with the program ( cheese ) it should be loaded already

if it does not come on do this
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each 1

if your computer starts to run hot or the fan runs fast
open cheese's help click the faq's 
it will bring up the same popup window
it tells you to set the video ,plugin to,x window system (no xv)
as for the driver im not sure you need it now days

---

### Post by Jarmen_Deffs on 2010-03-08
> **no2498 said:**
> try your cam with the program ( cheese ) it should be loaded already

if it does not come on do this
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each 1

if your computer starts to run hot or the fan runs fast
open cheese's help click the faq's 
it will bring up the same popup window
it tells you to set the video ,plugin to,x window system (no xv)
as for the driver im not sure you need it now days

I don't think Cheese is installed by default.

In the main menu go System > Admin > Synaptic, then type in cheese, tick the box, etc, to install it.
It should then appear in Sound & Video in the main menu. (I think?)

---

### Post by djr80 on 2010-03-09
Wow - you guys are geniuses!!!

Cheese gets the webcam working.  Next question: how do I get  the camera working in skype?  When I go to options and click on the test under video call options, nothing happens.  Any thoughts?

Thanks so much for your help!

---

### Post by no2498 on 2010-03-09
your on your own with skype
try it in ekiga softphone or msn just get it working first

---

