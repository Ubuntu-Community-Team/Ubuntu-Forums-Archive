---
title: "Why is my sound so low?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by natman on 2009-04-25
I have Kubuntu 904 running and my sound is a little weird, if i bring it down to <30% any sound is essentially impossible to hear if so low, i seem to have to leave it at 90+ % the whole time. In windows 45% suits me just fine and i have that much extra volume when i need it. Is there a reason for this?
Thanks:
Patrick

---

### Post by dlm4849 on 2009-04-25
Run alsamixer from the terminal and check that all apropriate volumes are up.

---

### Post by natman on 2009-04-25
Yeah they all seem to be up fine, here is a shot of my window.

---

### Post by charafantah on 2009-04-26
Same problem :) using Kubuntu 9.04 on Lifebook E series, HDA Intel.

you can barely hear the sound at 100%, checked alsamixer and all is 100%, windows XP on same machine is working just fine.

---

### Post by OMJD on 2009-05-04
I'm having this exact problem. And all of my volume bars are up to max in alsamixer.

Anyone know of a fix?

---

### Post by kansasnoob on 2009-05-04
Look for the "VIA" toggles! They're not there by default but you can find them - I don't have a Kubuntu to try and find how, but even in Kubuntu you should be able to install gnome-alsamixer.

Don't use the terminal (just in case it would break something), but go to synaptic and install gnome-alsamixer (if it doesn't require the removal of some essential package(s).

Then look at the last four toggles! The VIA toggles!

---

