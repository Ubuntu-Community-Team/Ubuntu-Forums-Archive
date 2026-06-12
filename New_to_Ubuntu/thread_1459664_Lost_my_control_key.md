---
title: "Lost my control key"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by robertrose6 on 2010-04-21
My control key has stopped working. I have no idea when or why. Can some point me in a direction? I have made sure that it wasn't the program. I noticed it on tomboy but tried open office any it doesn't work there ether. 
This is on a HP G60-235. I do have compiz running. if there is any other info that will help please let me know and I will get that to you as so as I can.


Thank You

---

### Post by _0R10N on 2010-04-22
Well you could try starting up your system to a terminal, instead to gnome. Then run ```
showkey
```
Once the program is running, press the Ctrl key. It should display 29 for the left Ctrl key and 97 for the right Ctrl key. If those aren't the results you obtain, then there's a mapping problem.

Kind regards!

_0R10N >>

---

### Post by QIII on 2010-04-22
If you get nothing at all...

Do you have a spare keyboard that you are sure is working?  Eliminate hardware failure.

---

### Post by robertrose6 on 2010-04-22
> **_0R10N said:**
> Well you could try starting up your system to a terminal, instead to gnome. Then run ```
showkey
```
Once the program is running, press the Ctrl key. It should display 29 for the left Ctrl key and 97 for the right Ctrl key. If those aren't the results you obtain, then there's a mapping problem.
 
Kind regards!
 
_0R10N >>
 
I just tryed the showkey and I got 29 and 97. at least now i know that it isn't the keyboard.
 
I just turned off compiz and my ctrl came back. So I guss I have to look there for my issue. Thanks for that command. It has got me moving in the right dir.

---

### Post by _0R10N on 2010-04-22
You're welcome!!! So, if is a compiz problem, then there's an effect bound to the Ctrl key who's messing around. Try deactivating all effects, and then activating them one by one. When you detect the effect causing the problem, see its configuration and change the key  binding.

My major candidate is the water effect!:eek:

Kind regards!

_0R10N >>

---

