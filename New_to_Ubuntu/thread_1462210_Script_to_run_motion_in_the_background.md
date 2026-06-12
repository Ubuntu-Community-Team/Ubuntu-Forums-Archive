---
title: "Script to run motion in the background"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by maxmouse24 on 2010-04-25
Hello everyone,
I am new to Ubuntu. I have installed Motion on my computer so that when I am away it can be a security camera. My girlfriend also uses this computer. She sometimes forgets to turn motion on when leaving and I don't always have time to VNC in to turn it on. Is there a way that I can set up a script so that it is always running? for example (start up when computer boots up. turn off when other programs need the webcam (empathy, skype, etc) and then auto start up motion again when the webcam is not in use?

BTW I am using Ubuntu 9.10 Karmic
Thank you in advance for helping someone who knows as little as I do.
This has been a great ride so far and I am glad I got rid of Winblows.

---

### Post by agnes on 2010-04-25
If Motion hasn't such an option itself...
An idea is, you could make bash script that first starts Motion.
(For starting an app in background, append an '&' to the command.)
Script would then run ```
top  -b -n 1 | grep skype
``` regularly (say every 3 seconds) to check if Skype is running (skype used as example).
If so --> 'killall' Motion. If not so AND Motion is not running, then --> start Motion.
Then add script to your Startup Applications.
Making this script shouldn't be very hard, just loops and if-statements, for further reference, check a bash tutorial.

---

