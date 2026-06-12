---
title: "keyboard disconnecting"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by RedOctober on 2010-02-18
I have several computers running ubuntu 9.10.  They are all the same hardware, (new, purchased 1 month ago).  Only 2 of the bunch have this problem.... several times during the day, the computer stops responding to the keyboard.  The mouse still works.  We are using rdesktop to remote into a Win2003 server.

On the two computers that have the problem, they each have a different keyboard, and, the computers that don't have the problem some of the same keyboard as each of the ones that do have the problem, so it's not the keyboard.

The user has been rebooting the computer, but I discovered that if, by using the mouse and selecting menus, I can get GEdit to start, it somehow re-establishes the connection with the keyboard and I can type in GEdit, then I can type in all other apps as normal.

Any ideas on what could be causing this?

---

### Post by cariboo on 2010-02-18
Is there anything showing up in /var/log/Xorg.0.log or ~/.xsession-errors?

---

### Post by RedOctober on 2010-02-19
I'm not versed in what I should be looking for in the log files, but, reading through them, nothing jumps out at me like "keyboard error".  However, I think I made progress, I switched the Video Effects to "None" and after that we have been disconnect free for 2 solid days.  Which is really good.  It used to disconnect several times per day.  Maybe that was the problem.  Thanks for your help anyway.

---

### Post by RedOctober on 2010-02-19
Correction:  System/Preferences/Appearance/Visual Effects tab: set to "None".

---

