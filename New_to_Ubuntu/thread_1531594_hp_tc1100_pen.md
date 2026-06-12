---
title: "hp tc1100 pen"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by redbook4574 on 2010-07-15
How do I enable the pen to input text to programs such as firefox, open office etc.

---

### Post by redbook4574 on 2010-07-17
Never mind bit of a duffer, for some strange reason I cannot input password for synaptic but everything else works.

---

### Post by gauravm on 2010-08-03
Hey this is from (link below) to enter passwords with pen/stylus:

[http://wiki.linuxquestions.org/wiki/TC1100]("http://wiki.linuxquestions.org/wiki/TC1100")

> GNOME's graphical su / sudo frontend, gksu, by default grabs the focus, keyboard and mouse to prevent malicious applications from capturing and then automatically supplying the password. However, this also prevents onscreen keyboards from working at the gksu prompt. To allow this, Use the gconf-editor program (usually in Applications -> System Tools -> Configuration Editor). Find the key /apps/gksu/disable-grab  and turn it on. This will prevent gksu from grabbing focus and all input. You can then input the password the normal way, using Xvkbd, GOK, OnBoard, etc. Be aware though that this is a potential security vulnerability.


---

