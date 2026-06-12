---
title: "Bunch of small problems"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by TRouBLe32 on 2010-02-07
1. Two monitors[solved]
I have the nVidia driver ver.185 installed but the X Server Settings program can't save the X configuration file. I can apply the settings for the second screen just fine, it's just that every time i reboot i have to set it up again.

2. Mouse
I have set the mouse sensitivity and acceleration from the mouse utility to the lowest and the mouse is still WAY too fast. It gets on my nerves because i can't center the mouse correctly.

3. Network
Network and internet are connected, it's that the browsing is too damn slow. The pages load somewhat slow, but the streaming and downloading are killing me! Tried Firefox/Opera/Chrome.

Any help would be really appreciated!!

---

### Post by Greenwidth on 2010-02-07
For 1:
You need to run it as root:
```
sudo nvidia-settings
```
You should then be able to save to config.

---

### Post by marshmallow1304 on 2010-02-07
It's generally preferable to use gksu/gksudo to run graphical programs as root in Gnome, so
```
gksudo nvidia-settings
```


Does your mouse have multiple DPI settings?

---

### Post by TRouBLe32 on 2010-02-07
> **Greenwidth said:**
> For 1:
You need to run it as root:
```
sudo nvidia-settings
```
You should then be able to save to config.

Thanx! It still wouldn't save the file but now it shoed me a preview and i saved it mannually.

---

### Post by TRouBLe32 on 2010-02-13
Does anyone have some insight to my problem(s)??:p

---

### Post by oldos2er on 2010-02-13
For Firefox, see [http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1)

---

### Post by mechro on 2010-02-13
Mouse...

In a Terminal do **xset q**

This'll give your mouse settings under Pointer Control...

Try changing the acceleration and threshold settings with **xset m 5/10  1**... 5/10 and 1 are just examples: change the first number(acceleration) to a whole number or a fraction; change the second number(threshold) to a whole number. Read **man xset**:mouse section for explanation.

If you get a setting that works you'll have to figure out a way to get that setting to stick at Log-in. I can't help you with that as it needs to be configured in HAL or the X system which is beyond my knowledge.

---

