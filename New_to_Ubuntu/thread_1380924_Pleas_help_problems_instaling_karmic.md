---
title: "Pleas help problems instaling karmic"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by sxmaxchine on 2010-01-14
i have been trying to instal 9.10 on my desktop and it loads the first part were it asks if u want to instal, try ubuntu and the other things. however after i try both try ubuntu and instal ubuntu it loads the glowing ubuntu logo and after that my monitor says resolution out of range how can i fix this problem

---

### Post by MooPi on 2010-01-14
Try the alternate install CD. May let your machine get past the sticking point.

---

### Post by halitech on 2010-01-14
sounds like it's trying to run in a resolution that your monitor doesn't support (ie 1600x1200). What type of video card and monitor are you using?

---

### Post by sxmaxchine on 2010-01-14
thanku for the help moopi i might have to try that wen i get more internet cause i already used 700mb getting the desktop iso


also my monitor is an old compaq crt monitor and its resolution is 1024x768, and my graphics card is an nvidia geforce 7300 gt 512 mb ddr2

---

### Post by halitech on 2010-01-14
I think thats the problem, your monitor will only handle 1024x768 but the card wants to run natively at a lot higher resolution (maybe as high as 2560 x 1600). There should be an option when you first boot up to select additional options (F4 I think) that should allow you to boot into safe graphics mode that will hopefully allow you to install and then we can configure the video to work with the monitor.

---

### Post by sxmaxchine on 2010-01-14
ok i wil try that now thanks for helping

---

### Post by halitech on 2010-01-14
welcome, hopefully that will work for you. keep us updated

---

### Post by sxmaxchine on 2010-01-14
i tried it in safe graphics mode for both install and try mode but i still got the same problem do u have any other ideas

---

### Post by halitech on 2010-01-14
if the cd you have has an option to do a minimal install you could try that and then build up what you need from there. If it doesn't then you will need the alternate install cd and use it to install and then we can fix xorg to work properly with your card.

---

### Post by sxmaxchine on 2010-01-14
thanks for all the help i dont think my disk has the minimal option but i did find a keyboard shortcut that helped my you can use ctrl+alt+ + to increas res or ctrl+alt+ - to reduce res

---

### Post by ghostborg on 2010-01-14
Not much help.
I had a problem in the past , I can't remember exactly, but when I got the out of range message my monitor locked up and I had to unplug the power cord to reset it. I'm not sure but I think the problem was a loose connection as I only tightened one of the monitor cable screws.

---

