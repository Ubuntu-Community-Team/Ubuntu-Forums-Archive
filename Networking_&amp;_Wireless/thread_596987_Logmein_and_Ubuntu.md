---
title: "Logmein and Ubuntu"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by steven_vo on 2007-10-30
I am a new kid of Ubuntu 
Im using Ubuntu for OS choice and Logmein for network remote tool
What i see is using Logmein with Ubuntu is slowly than in Windows OS ?
Any one can explain to me, please ?

---

### Post by Steve1961 on 2007-10-30
Windows computers installed with logmein can be accessed in a browser that uses an activex control.  This seems to provide the fastest and most configurable option, and activex can be set as the default access method in the logmein control panel.  However, because Linux doesn't support activex, logmein is forced to rely on a java applet instead.  I've found this slower and less configurable than the activex plugin, but if you change the default preferences from activex to mozilla it still works reasonably well.  

I believe a Linux version of the logmein client is planned at some point, and I'm hoping that this will improve cross-platform functionality.  In the meantime, and because I use logmein to support some of my clients, I've found that the best solution is to run a copy of XP in Virtualbox and to use that exclusively for remote support.

---

### Post by snowlad on 2007-11-06
Well I would hazard to say that I am an even newer kid to Ubuntu... 1 week in but I had the same question/problem and believe for a new windows convert the following is a more familiar/easier solution.

1] Install WINE
2] Download a portable version of Firefox for Windows
3] Access as before using Firefox for Windows in WINE

I can expound on the above if neccesary...

This worked better for me than using their legacy java support.

---

