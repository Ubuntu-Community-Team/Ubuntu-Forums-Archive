---
title: "unity 2d and 3d :whats the difference?"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by werty2010 on 2011-05-13
whats the difference?
how to find out which one does my system use?

---

### Post by rosencrantz on 2011-05-13
3D needs accelerated graphics and compiz, which some cards or drivers are not capable of. 2D is a 'flattened down' version without special effects.
However, 2d is not in the standard live system, so, if you didn't install it specifically, you'll not be running it.
Try the output of top (console) or any other system monitor to see which unity version is running. Also, if there's a compiz instance and if there are lots of funky desktop effects (cube, wobbly windows, etc.), you are with high probability running 3d.

---

### Post by hockeybum27 on 2012-08-22
what do you mean when you say

*try the output of top (console) or any other system monitor*

Also, at the login screen, when I click on the Ubuntu logo next to my name, I have options for
> 
Cairo-Dock (Gnome + Effects)
Cairo-Dock (Gnome with no Effects)
Cairo-Dock (Unity)
Gnome-Classic
Gnome-Classic (no effects)
Ubuntu
Ubuntu 2D


I used to think 2D was better than Ubuntu, but now I'm thinking
Ubuntu = Unity 3D
Ubuntu 2D = Unity 2D

Also does using compiz-settings-manager (ccsm) turn off Unity or any of these?

---

### Post by Bufeu on 2012-08-22
[http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d](http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d)

---

### Post by Carborundum on 2012-08-22
> **hockeybum27 said:**
> what do you mean when you say
I used to think 2D was better than Ubuntu, but now I'm thinking
Ubuntu = Unity 3D
Ubuntu 2D = Unity 2D

That is correct.

> Also does using compiz-settings-manager (ccsm) turn off Unity or any of these?
Simply *using* ccsm won't by itself turn off Unity, but you can easily break Unity with ccsm if you don't know what you're doing,

---

### Post by NikTh on 2012-08-22
> **werty2010 said:**
> 
how to find out which one does my system use?

Hi , 
you can open a terminal (ctrl+alt+t) and paste these commands 
```
echo $DESKTOP_SESSION
``` 
or 
```
env | grep DESK
```
and from the output of commands you will understand.
Thanks

---

