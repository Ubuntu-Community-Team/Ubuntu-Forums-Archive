---
title: "Mini DV capture problems"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Zaphou on 2010-05-09
Hey all,

I've been looking around the Forums for about a week now and can't find a solution to my problem.

I changed to Ubuntu Lucid Lynx from Windows XP and I'm trying to capture video and sound from my Panasonic Mini DV NV-GS280 Camcorder, I do not have a firewire so I'm using a USB.

I have installed Kino and DV Grab, however whenever I plug my camera in, it immediately picks it up as a webcam, which seems to be the opposite of everyone elses' problems. It does not appear as a device like my other USB connected devices do.

I think I need to open a port of some sort, or get a specific driver for my camera, yet corporate OSs strike again as the disc I have only works on XP, and wine won't pick it up.

Does anybody else have this problem?

I am a complete beginner with the skills on ubuntu as a snail has at walking, so write very slowly please

Thank you in advance

---

### Post by applehead on 2010-05-09
If it's any help, I tried using usb with all kinds of problems.

bought myself a fie wire capture card really cheap and had no problems at all.

---

### Post by no2498 on 2010-05-09
let see if ubuntu sees the cam

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

if it come on
try it in cheese

btw windows cd's do not load on ubuntu/linux

---

