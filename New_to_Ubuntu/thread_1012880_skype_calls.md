---
title: "skype calls"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by chris200x9 on 2008-12-16
I am using a macbook and I have followed this guide to get skype calls working [http://ubuntu-tutorials.com/2007/12/30/microphone-support-on-the-macbook-skype-2-supported/](http://ubuntu-tutorials.com/2007/12/30/microphone-support-on-the-macbook-skype-2-supported/) but everytime I try to make a call I get the message problem with audio playback and the call automaticaly quits.

---

### Post by Golem XIV on 2008-12-16
I had a similar problem, though not on a Mac.

Open Skype options and go to the Sound Devices section.

Change the configurations from Default Device to other options - I can't tell you exactly which ones because I don't have the same system, but try "pulse" for both Sound Out and Ringing and whatever your hardware is on channel 0 for Sound In (mine is "hw:nvidia,0")

Play a bit with it and see if it helps.  Good luck.

---

### Post by chris200x9 on 2008-12-16
not to be dumb but where doI find the sound device section? edit: found it

thanx it works!

---

