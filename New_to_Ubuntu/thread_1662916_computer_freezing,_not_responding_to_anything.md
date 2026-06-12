---
title: "computer freezing, not responding to anything"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by venicequeen7706 on 2011-01-08
I have been using ubuntu for a year now and maverick since it was released and never had my computer freeze until a two weeks ago. Now it is freezing every day or two. when I say it freezes, I mean it will be working normally, then suddenly absolutely nothing works. The mouse does nothing, the keyboard does nothing, the button to shut down does nothing. I end up having to turn off the power and turn it back on. I have no idea what may be causing this. It seems to happen at random and often the computer is running only one or two programs at the time, so it isn't freezing because it is over worked. any help would be great

---

### Post by cipherboy_loc on 2011-01-08
Two questions:

1) What updates have you installed recently? Any kernel upgrades? In Synaptic:
File -> History. Look at the history from two weeks ago (About the time when you started noticing the freezing).

2) Does one piece of software trigger it (Is OpenOffice.org always running when it freezes for example), or does it happen with multiple pieces of software?

3) How old is your computer? Is it possible that the CPU is over heating? Though usually the system either crashes or remains responsive to the power button...


Cipherboy

---

### Post by venicequeen7706 on 2011-01-08
1. according to the history, I haven't installed anything new since November.

2. I'm not sure. This time firefox was the only thing running, and I'm sure it was running a few of the other times. I think open office was also running a few of the times.

3. the computer is 5 years old. I use a computer temp monitor from synaptic to make sure the computer doesn't get too hot. I rarely ever let it get about 70 Celsius.

---

### Post by azertyh on 2011-01-08
hello,
recently, there was a kernel update. during startup, select another kernel in grub, the previous for example, and see if your computer still freezes.
above 50°C, it's already too hot.

---

### Post by Neobuntu on 2011-01-08
Boot a live CD. If no problems, it's probably software.

If you have similar problems, it's likely all hardware.

---

### Post by venicequeen7706 on 2011-01-09
> **azertyh said:**
> hello,
recently, there was a kernel update. during startup, select another kernel in grub, the previous for example, and see if your computer still freezes.
above 50°C, it's already too hot.


My computer does load the grub menu, it goes straight to the login. how do i get to the grub menu?

---

### Post by azertyh on 2011-01-09
to load the grub menu, press SHIFT key during the startup, before the GDM (the login window).

---

### Post by venicequeen7706 on 2011-01-26
I have tried two older kernals and the one released since I first posted and this is still happening. It seems like more often than not, it happens when I move my laptop, which seems to me to imply it is hardware, but I have no idea what it may be. any ideas? 

on another note, someone mentioned 50c is too hot, but my computer is never under that, even when the computer has just started

---

