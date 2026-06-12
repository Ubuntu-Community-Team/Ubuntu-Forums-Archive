---
title: "RSEIUB problem - 64 bit Intrepid"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Michael Dooley on 2009-03-12
At the moment, I have two physically seperate machines, one running a fully updated 8.04 install and the other running a fully updated 8.10 64 bit install. Both machines are multi boot if that helps at all. On the Hardy Heron machine, all key operations appear to work and once or twice a week I can/must reboot using the (left) Alt-SysRq + [RSEIUB] keyboard combination. This keyboard is a PS/2 (old Dell) keyboard which seems to work fine. Other than a mouse movement causing the entire system (kernel?) to freeze, things have been going well.

Slightly off focus - By the way, on my last Skinny Elephants with the Hardy machine, the dialer software (I connect using Conexant winmodems in both machines) was using an abnormal amount of CPU resources, if that is of any interest.

Problem - On the 64 bit Intrepid Ibex machine, which has been running for maybe two or three weeks, Raising Skinny Elephants does not work, but instead gives me multiple instances of pressing Print-Screen (Save Screenshot). This machine has a USB keyboard and mouse with no PS/2 ports. Moving the mouse alone will not restore my session from the screen saver but tapping on the spacebar works. 

Ctrl-alt-f1 and ctrl-alt-backspace appear to function on the 64 bit installation but Raising Skinny Elephants doesn't work, even upon a fresh reboot. Is there a keyboard setting I should change? What else could I do to investigate this situation?

Thanks for providing any insights...

---

### Post by philinux on 2009-03-12
Check under system>prefs>keyboard>layouts. Make sure it's set correctly.

---

### Post by Michael Dooley on 2009-03-12
Changing the keyboard layout doesn't appear to affect the problem. Both machines were set to Generic 105-key. Using Keyboard shortcuts to disable the Alt-PrintScreen combo eliminated the multi instances of Screen Save though.

Thanks Phil.

-----------------------

Additional information: I used Ctrl-Alt-F1 to drop into a virtual terminal. In there, Alt-SysRq + [RSEIUB] worked - i could directly see the actions of each key combination.

I checked in the extremely simplified Dell bios and none of my changes in the USB settings of the bios let RSEIUB work in X. I bet another motherboard with PS/2 ports would bypass this vexing situation. 

I'd like to find a solution though.

---

### Post by Michael Dooley on 2009-05-04
Update:

64 bit Jaunty provided a Dell USB keyboard selection that allows RSEIUB to function. Not all is well with my 64 bit installation but at least there has been some improvement.

---

