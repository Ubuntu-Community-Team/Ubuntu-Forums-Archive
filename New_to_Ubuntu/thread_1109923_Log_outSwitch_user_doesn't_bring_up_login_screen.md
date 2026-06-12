---
title: "Log out/Switch user doesn't bring up login screen"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-29
Whenever I log out or go to switch user, the computer goes blank, runs some text about shutting some things down and then at the point where it should show the screen again instead it shows a blank screen and the light on the caps lock key flashes (kernel panic) until I have to hard-restart the computer.

I think this is a problem with the GUI not restarting, because when I go into virtual console and then try to return using ctrl+alt+F7 I get the same problem - a blank screen instead of a GUI.

The login screen works when the computer starts up for the first time, and suspend/resume works fine.

Relevant information:

Compiz-Fusion, ATI proprietory 9.3 catalyst drivers, backports enabled, shiki-colors theme installed, Firefox 3.0.8

---

### Post by humphreybc on 2009-03-31
bump... I'd quite like to get this fixed.

---

### Post by humphreybc on 2009-04-03
Anyone??

---

### Post by SunnyRabbiera on 2009-04-03
I have had similar issues, thats why I dont use the fast user switch applet.
Though the kernel panic... not good.

---

### Post by asmoore82 on 2009-04-03
My information is much-dated -
but similar problems with suspend/resume used to be a known issue with ATI's drivers.

That was back around Ubuntu 7.10 Gutsy, though.
You could try turning off the ATI driver just to see.

---

### Post by sirwhiteout on 2009-04-09
I run Intrepid on a Toshiba Satellite PSAFGE with the ATI Radeon X1200 card, and I have exactly the same problem.

Removing the proprietary driver got user switching and log out working.

Time to send a bug report to ATI... :-?

---

