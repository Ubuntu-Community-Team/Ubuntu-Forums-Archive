---
title: "Very slow Adobe Flash Player"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by flue on 2010-03-24
For weeks I've been trying to fix the sluggishness of Adobe flash in Ubuntu 9.10, videos play fine but when the kids go to one of their flash game sites FF is herky jerky.  6yr old twins can really really get on ones nerves when they can't get their games to work. :(  

Finally I snapped, figuratively anyhow.  I've been having issues with FF on M$ for some time being a HUGE memory hog. Working through all the suggestions on these forums and other "blogs" resulted in very little improvements for me. Long story short, I started researching "Other" browsers.  

And found Epiphany.  WOW what a difference!  If your having problems with Flash and nothing seems to work, give Epiphany a shot.  You may be pleasantly surprised.  Couldn't even begin to tell you why it works 1000% better than FF flash, but it does...for me.

---

### Post by Patrick70 on 2010-04-01
Didn't work for me, I'm afraid... I also have Ubuntu 9.10 and Flash remains awfully slow no matter what I try.

---

### Post by no2498 on 2010-04-01
would like to see what plug in you two have in gstreamer-properties
the one it is set to now ?
open a terminal type gstreamer-properties click enter
click video
what is your plugin set to

---

### Post by Patrick70 on 2010-04-08
> **no2498 said:**
> would like to see what plug in you two have in gstreamer-properties
the one it is set to now ?
open a terminal type gstreamer-properties click enter
click video
what is your plugin set to

Well, since then I removed my original installation of Ubuntu 9.10.
I have now reinstalled the  64 bit version of 10.04 Beta1 on a dedicated partition and installed the Flash player via the software center.
I see a great improvement to what it used to be, but it is still slower compared to Vista.


As for your question, with my current installation the video output plugin is set to 'Autodetect'. I will play around with those settings a little to see if it makes any difference at all.

---

### Post by Patrick70 on 2010-04-08
I quickly tried several combinations, but it doesn't seem to make any difference.

However, when I run the gstreamer-properties in the terminal, I get the following message:

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'


Would I need to install any of these to get things to work better?

---

