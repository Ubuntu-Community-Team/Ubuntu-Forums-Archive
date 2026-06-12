---
title: "Is Jaunty booting properly ?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by ericstrom on 2009-07-05
What is the proper sequence for Jaunty boot up. Should the splash screen come up and stay up while going through all the steps involved in booting or should it come up for a while and then disappear and the screen go black for a while until Jaunty is fully up and the welcome sound starts ?

I currently get the splash screen for 10 to 15 seconds and then the screen goes black (with the exception that I see my mouse cursor) for another 20 to 25 seconds. After that period I get the welcome sound and Jaunty is up and running. Is that the way it's supposed to work or is there a bug in the boot sequence somewhere ? It seems odd that the splash screen would disappear and go black for 20 to 25 seconds.

---

### Post by JillSwift on 2009-07-05
That's not normal, no. I'm guessing something is messing with video when it starts - possibly the video driver for X.

Tell us more about your hardware and drivers.

---

### Post by ericstrom on 2009-07-05
Jill, I occasionally have problems with video so that sees like it could be it. Not sure what to tell you about my system. It's a few yrs old ....AMD 2200+ processor with Asus motherboard. No separate video card...using what's on the motherboard. Dual booting WIndows XP and 9.04...but rarely using XP.

ASUS A7V8X-X ACPI BIOS Revision 1009
system.firmware.vendor	Award Software, Inc. 
AMD Athlon(TM) XP 2200+
pci
info.product	VT6102 [Rhine-II]
info.vendor	VIA Technologies, Inc. 
Maxtor 40 GB hard drive  MAXTOR 4K040H2 

Any suggestions ? (other than get a new PC :-)

---

### Post by LewRockwell on 2009-07-05
It has been my experience over quite a range of operating systems that each such system does it's "own thing" with respect to boot screens, splash screens, and how they each "load up" and any number of them do "strange" things

My first inclination would be towards screen changes from a "safe" and/or "generic" resolution during boot-up, to the "running" configuration

Does your system exhibit the same characteristics with several different video display devices?

.

---

### Post by ericstrom on 2009-07-05
"Does your system exhibit the same characteristics with several different video display devices?"

How would I test that ?  I only have one display device...my Dell monitor.

---

### Post by ivanvajar on 2009-07-05
Boot sequence is not the same on every computer. Did you have any problems while using Ubuntu once it boots?

---

### Post by LewRockwell on 2009-07-05
> **ericstrom said:**
> "Does your system exhibit the same characteristics with several different video display devices?"

How would I test that ?  I only have one display device...my Dell monitor.

As is most often the case, my commentary is more for the general reference of all present and future viewers of the topic/thread than it is for any one specific poster.

With respect to video display devices, nowadays they are dime-a-dozen and more often than not can be found with relative ease, both for brief periods of experimentation/testing and as a back-up to store in the closet, basement, garage, or attic for those times when you find one necessary(especially for those midnight fix-it sessions that we all enjoy so much).

.

---

