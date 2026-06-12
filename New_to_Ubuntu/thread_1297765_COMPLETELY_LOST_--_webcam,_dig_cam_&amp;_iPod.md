---
title: "COMPLETELY LOST -- webcam, dig cam &amp; iPod"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by jdee5287 on 2009-10-22
I'm pretty new to Ubuntu and everything and loving it so far...I've got a rocketfish webcam that I've been trying to work, but my computer doesn't show its even connected. I've read SO many help things on here and either they don't apply to me or I have no idea what there talking about.  My computer doesn't do anything for my iPod when its plugged in on Windows side (only place for iTunes) of my computer.  And lastly my Sony Cybershot camera when thats plugged in it doesn't do anything either -- no icon pops up, no indication that I even have it plugged in shows up. dig and web cams both don't show up in both windows side or ubuntu side. 

I've tried plugging in mouse and printer which both use USB ports and they work perfectly and it both Windows and Ubuntu.

---

### Post by tarps87 on 2009-10-22
Can you plug the web cam or camera in, then applications -> accessories -> terminal

```
lsusb
```
and post the output here.

I pods may be a little more tricky, what model do you have?

---

### Post by revanb on 2009-10-22
How old is your computer?

If you get no response in either Ubuntu or Windows then it may be a hardware problem. It may be that the items not picked up are USB 2.0 devices and your hardware USB 1.1 or something like that?

I'm not an expert on USB, but I know my old PC doesn't recognise my current 8Gb USD pen drive.

Good luck!

---

