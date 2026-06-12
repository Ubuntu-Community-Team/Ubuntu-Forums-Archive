---
title: "Samba Problems"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by Jvaldezjr on 2007-09-08
Anyone having problems with Samba in Feisty?  I'm noticing that KDE wipes my share settings when I reboot my machine- because when I do so, I can no longer connect to my shares from my XP computer.  When I investigate further I find that some of the settings were reset.  Either the KDE applet is not saving the options I choose, or its a SAMBA problem.

---

### Post by x64Jimbo on 2007-09-08
Check the link in my sig for help on setting up SAMBA shares properly. For the most part, if you want it done right you still have to tweak config files. It's not complicated, but it's different from setting things up in Windows.

---

### Post by scxtt on 2007-09-08
if you have shares on your ubuntu box that you're connecting to from XP and you can't connect after reboot, you should be sure the samba service is set to start on boot for the run-level you boot into ...

---

