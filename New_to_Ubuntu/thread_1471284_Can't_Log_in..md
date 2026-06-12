---
title: "Can't Log in."
date: 2010-05-03
forum: New to Ubuntu
---

### Post by bandersen on 2010-05-03
I uninstalled pulse audio through synaptic, and installed Esound. I rebooted and I can't log in to my user account on Ubuntu.

---

### Post by nmaster on 2010-05-03
does the login screen appear at all?

---

### Post by bandersen on 2010-05-03
Yes, it does. But when I log in, the login sound comes on but then the log in screen re-appears.

---

### Post by ajgreeny on 2010-05-03
Did you note what else was removed along with pulseaudio?  When I do the removal request without actually removing it, I can't see anything that should affect the login activity, but perhaps your setup is different from mine.

What version of ubuntu are you running?  How did you remove pulseaudio?

---

### Post by ranch hand on 2010-05-03
Have you tried booting to recovery mode?

I would try that and when you get to the menu screen select the "dpkg fix broken packages" option.

When that finishes and you return to the menu screen select the "return to normal boot" option.

You will probably get a text login.  Inter your user name and on the next prompt enter your password.

On the next prompt enter   startx   and that should take you to your desktop.  You can use this method of logging in until you get this straight.

When you are in you should check synaptic and see if there are any broken packages listed.

---

