---
title: "Why does my processor max out when watching online video?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by iNeeed on 2008-12-22
Why does my processor max out when I watch online videos?
This happens when they've already buffered/when they've downloaded. (meaning the little grey bar completes to the end of the line.)
It runs fine for a while but then it gets all choppy and I lose control of the controls.(it takes a while for me to even stop the video) So I checked the processes and realized that the cpu usage increases dramatically while this is happening.
I'm curious?
I want to know everything I've ignored.

---

### Post by jimmy the saint on 2008-12-22
when this is happening did you look at the system monitor and see which process is using all the juice?  It will probably be npviewer, but you should check and make sure.  Flash is pretty processor intensive, but I have never experienced that. How did you instsall flash?  Try purging the package that you installed and reinstalling it.

Check processes:  System>administer>system monitor

to purge:  Open synaptic, select the package and select completely remove.

---

### Post by iNeeed on 2008-12-22
> **jimmy the saint said:**
> when this is happening did you look at the system monitor and see which process is using all the juice?  It will probably be npviewer, but you should check and make sure.  Flash is pretty processor intensive, but I have never experienced that. How did you instsall flash?  Try purging the package that you installed and reinstalling it.

Check processes:  System>administer>system monitor

to purge:  Open synaptic, select the package and select completely remove.

Firefox was the one using the most.  I'm going to check it out again in the morning.  I've run out of time to mess around with this tonight.  Thanks for your advice!  Will totally get into it after some zzzz's.

---

### Post by kostkon on 2008-12-22
> **iNeeed said:**
> Firefox was the one using the most.  I'm going to check it out again in the morning.  I've run out of time to mess around with this tonight.  Thanks for your advice!  Will totally get into it after some zzzz's.
Yes, *Flash* is the culprit even if in *System Monitor* only *Firefox* is shown.

Try right-clicking on the *Flash* video/applet you are watching/running, go to *Properties* and in the first tab check if the *Hardware Acceleration* option is enabled.

---

### Post by iNeeed on 2009-02-07
> **kostkon said:**
> Yes, *Flash* is the culprit even if in *System Monitor* only *Firefox* is shown.

Try right-clicking on the *Flash* video/applet you are watching/running, go to *Properties* and in the first tab check if the *Hardware Acceleration* option is enabled.

Yes, hardware acceleration is enabled.  I tried unchecking the box, but it won't uncheck.

---

