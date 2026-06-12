---
title: "Dual Monitor Problems"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by rr54 on 2010-08-29
Hello, 

I'm new to here (and to Ubuntu). I got fed up with XP running slowly on my Laptop (its getting old and struggling a bit) so thought I would give Ubuntu a try.

I have an extra monitor plugged into my laptop, however I can't seem to get it working properly with Ubuntu.

I tried messing about with the monitor settings (in SYSTEM>PREFERENCES>MONITOR), however have had no luck.

This thread may be about something similar, however I was unable to gain anything from it.

[http://ubuntuforums.org/showthread.php?t=1468484](http://ubuntuforums.org/showthread.php?t=1468484)

My second screen can be set as an extension of my first screen however it is all wavy and the image on the screen won't stay still.

I have a Dell Inspiron 9400 with a ATI Radeon Mobility X1400 graphics card connected to the secondary monitor using a VGA cable.

The laptop screen displays fine, and I can set the external monitor to the primary display and this works fine too, however when I try to split my desktop between the two the external monitor as I said above goes wavy.

Any help would be much appreciated, note that I am a complete novice with Ubuntu.

Thank You

RR54

---

### Post by gordintoronto on 2010-08-29
Are you using Ubuntu 10.04? Is it correct that Administration/Hardware Drivers does not offer you a video driver? Have you looked at the manual for your computer, to see what it says about external moniotors? If the manual has been mislaid, you can download it from the Dell web site.

I probably can't help you much, but other people may be able to, with a bit more information.

---

### Post by rr54 on 2010-08-30
Hi, 

I found a solution. I needed to install xorg.driver.fglrx in the synaptic package manager, then restart to get the ATI Catalyst Control Centre working.

Now I have my 2 monitors up and running:).

Thanks.

---

### Post by gordintoronto on 2010-08-30
Thanks for posting the solution!  You could use the Thread Tools to mark this as Solved.

---

