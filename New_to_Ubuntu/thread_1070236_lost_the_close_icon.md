---
title: "lost the close icon"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by loseby on 2009-02-14
When you open a window or even Firefox you have a minimise/close/resize button in the top right corner.

Now say in firefox I can go to full screen mode and it appears but then the screen sort of scrolls up and it disappears but if I move the mouse up it reappears

But I want the standard window to appear with the 3 selections in the top right hand corner. Dont know what I did to make this happen

---

### Post by ilioscio on 2009-02-14
can't you just right click below the 3 (min max close) buttons and uncheck "hide toolbars"

---

### Post by SunnyRabbiera on 2009-02-14
try F11?

---

### Post by ilioscio on 2009-02-14
my mistake, I thought you wanted fullscreen firefox without the top bar disappearing. :P thanks SunnyRabbiera

---

### Post by loseby on 2009-02-15
I know f11 will make firefox full screen but it wont for the other applications. I dont know why the 3 application buttons have disappeared as a default option but its annoying the hell out of me. 


and clicking below where the 3 buttons and unticking hide toolbar should be doesnt work

---

### Post by -kg- on 2009-02-15
Try this:

Launch Synaptics and do a search for "Compiz" (without the quotes, of course).  Install "Compizconfig-Settings" from the list.

Once installed, launch either by typing "ccsm" in a terminal window or clicking on "System/Preferences/Advanced Desktop Effects Settings."

Under "Utility" click on "Workarounds."  At the top of the list you will find "Legacy Fullscreen Support."  _Uncheck_ the checkbox, close ccsm, and see if that works.

This works for Firefox losing it's min/max/close buttons totally, but I'm not sure in your case.  It sounds like you're not losing them, but they move up out of view.

Anyway, something to try and see if it works.  Of course, all the above is assuming that you're using Compiz in the first place.  Compiz is included by default with Ubuntu, but there are other desktop effects managers that you can use in it's place.

---

### Post by loseby on 2009-02-15
actually turned of Compbiz well to be exact disabled custom and went back to exact in visual effects and all is working now


thanks for all the help

---

