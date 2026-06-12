---
title: "Power Management Problems"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by jezston on 2009-02-07
I have a Toshiba Tecra M2 which I've recently installed Ubuntu on.

I have set up in power management, that when attached via AC power the computer should never go to sleep, never turn off the display, and not even dim the display when left alone.

Problem is, it still does!

This is a real pain as I use the laptop as a jukebox of sorts, with Amarok displaying the artist and track in a big window in the centre of the screen, and I have this running at a music night I run. With the screen dimming and then turning itself off, this is a serious problem, especially if I jog the trackpad to make it come back on, the audio glitches momentarily.

Anyone know what might be causing this and how I can fix it?

---

### Post by jerrrys on 2009-02-08
i am not familiar with Toshiba, but i would say that if you have sleep mode set to never and it still sleeps that you need to look at bios

---

### Post by ibuclaw on 2009-02-08
When you go into
**System -> Preferences -> Power Management**

Under the **On AC Power** tab, are the "**Put computer to sleep**" and the "**Put display to sleep**" bars set to "**Never**" ?

Regards
Iain

---

### Post by mc4man on 2009-02-08
There's an xorg entry you can make that will prevent the display from going to sleep, don't have it handy ATM.

The other way is to go to screensaver and turn off the screensaver and set the time till computer is considered idle to less than the time it's currently going to sleep. (10 -15 min. is usually good.

Then set the powersaver to never.

The powersaving setting doesn't kick in till the computer is considered idle, this way before the bios sleep takes affect, powersaving is activated (never sleep

---

