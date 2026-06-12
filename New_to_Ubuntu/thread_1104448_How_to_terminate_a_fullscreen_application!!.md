---
title: "How to terminate a fullscreen application?!?!"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-23
Okay so I have been trying to get Urban Terror to work properly, and it works for a while but then all of a sudden my keyboard and mouse inputs freeze up after about 20mins of playing time. So, to quit I do this:

ctrl+alt+F2 to enter virtual console

login

"top" to enter the process manager

k [PID for Urban Terror]

then ctrl+alt+F7 to return to the GUI... but what I find is a black screen with my mouse pointer in the middle. It won't let me enter the GUI again.. I have tried absolutely everything and in the end I have to go sudo reboot to fix the problem.

This is absolutely ridiculous. How hard can it be to implement a ctrl+alt+delete GUI process manager such as in Windows that works FULLSCREEN as well as in the desktop!?!?

---

### Post by Joeb454 on 2009-03-23
Do you have any desktop effects enabled?

If so try disabling compiz and running the game again, to see if that's the root cause of your problem :)

---

### Post by VCoolio on 2009-03-23
also check if you have a screensaver enabled. If so, disable. This was my problem having your same issues but then with openarena.

---

### Post by humphreybc on 2009-03-23
Okay I just used the compiz-fusion icon to change to metacity and made sure my screensaver was disabled (it was on "blank screen" and I unchecked the "activate screensaver when computer is idle" box) and still no luck...

I must say I have had a lot of problems with the GUI/X. When the ctrl+alt+backspace key combo was enabled it would terminate my xorg process and kill the GUI but it just stayed on a black screen and didn't take me back to my login screen like it's meant to. And that was straight out of the box Ubuntu...

---

