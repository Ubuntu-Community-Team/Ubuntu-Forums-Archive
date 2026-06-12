---
title: "exiting my xserver to install display driver"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by DSK6 on 2009-12-09
Hi i am pretty new to ubuntu and i have been searching for a fix for my problem for a couple of hours now and i still haven found anything that looks like the problem that i am having i am trying to install nvidia drivers but before i can install them i need to exit my x server but i tried it first with ctrl-alt f1 or f2 and so on but when i try that i get a some kind of distorted screen with all kinds of green and blue vertical lines and i found a code to shut my x server completely down with sudo /etc/init.d/gdm stop when i do this i get the same distorted screen with the same kind of colored lines does anyone know what this is and how i can fix this ? 

Thx

---

### Post by wojox on 2009-12-09
Try:

CTRL + ALT + F1.

Now execute the following commands:

```
sudo service gdm stop
```

---

### Post by DSK6 on 2009-12-09
@wojox

as I told in my original post i already tried ctrl-alt f1 
and I already tried something similar to the code you posted but i have also just now tryed your code but i still have the same problem a distorted screen with green and blue vertical lines

but thx for your reply

---

### Post by DSK6 on 2009-12-10
So nobody knows what i am talking about or how to fix my problem ?

---

### Post by DSK6 on 2009-12-13
*SOLVED*

it appears that my nvidia graphic card was running in low graphic mode 
that was the reason for my distorted screen and those strange colors 
i solved it by going to a older kernel and fixed it from there 
and that solved my problem 

@Mods you can close it 

Thx

---

### Post by presence1960 on 2009-12-13
> **DSK6 said:**
> *SOLVED*

it appears that my nvidia graphic card was running in low graphic mode 
that was the reason for my distorted screen and those strange colors 
i solved it by going to a older kernel and fixed it from there 
and that solved my problem 

@Mods you can close it 

Thx

you can mark the thread as solved yourself by going top right of forum window to Thread Tools> select Mark this thread as solved

---

