---
title: "sensors-applet available for Ubuntu 9.10 64bit version?"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by Sepiraph on 2010-04-17
I was just running lm-sensors with the applet in the 32 bits version Ubuntu 9.10 earlier today.  Then I went and install the 64 bit version, re-install lm-sensors (which works) but now I can't install sensors-applet either using apt-get or Synatic.  The former I get error message:

> $ sudo apt-get install lm-sensors sensors-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
E: Couldn't find package sensors-applet

While it doesn't even show in Synaptic!

---

### Post by empty_spaces on 2010-04-17
Have you enabled the community repos (universe) in Software Sources?

Edit: To answer your question, yes, sensors-applet is available in 64bit, i'm using it.

---

### Post by Sepiraph on 2010-04-18
Thanks, I unchecked it before and now it's there. :P

---

