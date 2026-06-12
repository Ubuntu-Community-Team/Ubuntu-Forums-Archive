---
title: "My screen goes blank when I boot Ubuntu"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Spitfire1160 on 2009-03-16
I'm new to ubuntu and I’ve had a lot of problems with installing it with dual boot. Most of the problems were from my own lack of knowledge in this area. 
   So I booted up windows and installed the new ubuntu 8.10 x64 inside of my vista x64. I’ve tried out side of windows but it still does this and I have problems getting it to boot. When I boot into ubuntu the usual boot screen comes up with the ubuntu logo. After it Loads my monitor losses the signal and it's just blank. So I’m guessing it’s the video card driver or something. I've tried booting from the cd and it does the same thing.

   Any suggestions would be appreciated 
   Thanks

---

### Post by cmnorton on 2009-03-16
If you press CTRL+ALT+F1, do you see a text-mode login screen?

If you see a text-mode login screen after pressing CTRL+ALT+F1, do you see the graphical login screen after then pressing CTRL+ALT+F7?

---

### Post by arapa on 2009-03-16
Which video card do you have?

---

### Post by Spitfire1160 on 2009-03-16
i have a ATI Radeon 4850 and i have no integrated graphics card in my motherboard

---

### Post by arapa on 2009-03-16
Have you seen this bug?:

[[RV770 HD 4850] ATI Radeon HD 4850 not supported - white screen and system freeze]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/325394")

It looks like there may be a fix coming in 9.04.

What happens when you hit [CTRL] + [ALT] + [F1] keys at the same time, do you see anything?

---

