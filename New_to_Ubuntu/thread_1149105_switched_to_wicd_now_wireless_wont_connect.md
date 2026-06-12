---
title: "switched to wicd now wireless wont connect"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-05-04
i switched to wicd since i could not seem to get network manager to work with e17. now wicd will kind of connect to my wifi but at 0.00%

this is not an issue with my router since im using my girlfriend's computer as a control sample and that is connected 100%

and im currently in gnome with this issue as well

please help asap

---

### Post by PatrickMoore on 2009-05-04
reinstalling did not work according to wicd's forum its a python issue but the instructions provided point to a filepath i do not have on my system
usr/lib/python2.5/site-packages/wicd

this is entirely non existant

---

### Post by Mark Phelps on 2009-05-05
Know it's a long shot, but I encountered a python-related problem installing gdesklets on my 9.04 machine, and was told that it was related to different versions of python being needed.  The suggestion (which fixed my problem) was to install python-all.  You could give that a try.

---

### Post by clive littlewood on 2009-05-05
Hi

When I installed WICD it informed me that I did not have the appropriate python libs installed and offered to install.

Then WICD installed and has been very stable and much better than NM.

Try completely uninstalling from synaptic and then installing again.

Clive

---

### Post by imdano on 2009-05-05
> **PatrickMoore said:**
> reinstalling did not work according to wicd's forum its a python issue but the instructions provided point to a filepath i do not have on my system
usr/lib/python2.5/site-packages/wicd

this is entirely non existantWhat makes you think it's a Python issue?

---

### Post by Bodsda on 2009-05-05
Hi,

usr/lib/python2.5/site-packages/wicd   is missing a '/' try this one,

/usr/lib/python2.5/site-packages/wicd

Hope this helps,

Bodsda

---

