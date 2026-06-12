---
title: "Sound stopped working?"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by Strider11o7 on 2011-08-29
Everything was working fine up until a few days ago when my computer just stopped playing any form of audio except for the bongo at the login screen and the "boop" noise that is played when I try to test the speakers under Sound Preferences > Hardware.

I've had this same issue on this Dell Studio 15 with previous Ubuntu installations, but I can't seem to resolve this issue on 11.04.

Ubuntu's troubleshooting guide and googling around for people who had a similar problem proved to be of no avail this time. I appreciate any help.

---

### Post by cariboo on 2011-08-30
Check the Sound Preferences->Hardware profile and make sure you have Analog output set. I had the same problem, and the output profile was set wrong.

---

### Post by Strider11o7 on 2011-08-30
I've tried all the profiles (originally it was on Analog Stereo Duplex), still no good =/

---

### Post by Strider11o7 on 2011-09-01
Okay I found the problem. For anybody else googling this issue, make sure you check that your output is set to analog stereo instead of digital (unless you're actually using the digital output). Seems so obvious now especially since I was a tab away from solving this issue the whole time, but better late than never.

---

