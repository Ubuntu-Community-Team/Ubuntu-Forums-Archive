---
title: "Compiz Fusion Cube on Natty Narwhal"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by Joe Zuyuz on 2011-07-06
Hi Ubuntu forums! I am relatively new to Ubuntu and Linux in general, though I've been working with UNIX & Unix-like systems for many years, and I've been playing with Linux on and off for a couple years now. Some parts of Natty are really impressing me, especially some of the interface changes. Of course, I understand that with every major update, there will be hiccups. And there are. Unity doesn't seem perfectly stable and compatible yet, which brings me to the heart of my problem;

The compiz fusion desktop cube seems to be broken by the desktop wall configuration which puts the desktop viewports in a 2x2 square. And I can't turn it off. I unchecked "desktop wall", but that had no effect. Rather than a cube, I get a flat 3d plane. By dragging a window to the edge or quickly panning around, I can move left or right between the top viewports, however, I cannot access the bottom viewports in any way. Any idea what's going wrong?

---

### Post by CatKiller on 2011-07-06
Setting the General Options -> Desktop size to ```
Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 4
``` in CCSM should get your cube to behave like a cube.

You'll probably also want to enable the Rotate Cube plugin.

---

### Post by Frogs Hair on 2011-07-06
[http://www.linux-radar.net/enable-desktop-cube-unity-ubuntu-natty.html](http://www.linux-radar.net/enable-desktop-cube-unity-ubuntu-natty.html)

---

### Post by Joe Zuyuz on 2011-07-06
> **Frogs Hair said:**
> [http://www.linux-radar.net/enable-desktop-cube-unity-ubuntu-natty.html](http://www.linux-radar.net/enable-desktop-cube-unity-ubuntu-natty.html)

Ahhh!

Those were the instructions I followed, but Ubuntu crashed when I ran;

```
sudo service gdm restart
```

And I couldn't find the directions again, so I never got 'round to the part that says, "Adjust Number of Desktops"

Thanks!

---

### Post by beew on 2011-07-06
> **Joe Zuyuz said:**
> Ahhh!

Those were the instructions I followed, but Ubuntu crashed when I ran;

```
sudo service gdm restart
```And I couldn't find the directions again, so I never got 'round to the part that says, "Adjust Number of Desktops"

Thanks!

You can just logout and log back in instead of restarting gdm.

To set the number of desktop open CCSM, go to General > General Options and in the tab desktop size you can set the number of desktop. If you are using the cube set the vertical number to be 1, you can have as many as you want horizontally,--though it wouldn't be a cube anymore. :)

---

### Post by wildmanne39 on 2011-07-07
> **Joe Zuyuz said:**
> Hi Ubuntu forums! I am relatively new to Ubuntu and Linux in general, though I've been working with UNIX & Unix-like systems for many years, and I've been playing with Linux on and off for a couple years now. Some parts of Natty are really impressing me, especially some of the interface changes. Of course, I understand that with every major update, there will be hiccups. And there are. Unity doesn't seem perfectly stable and compatible yet, which brings me to the heart of my problem;

The compiz fusion desktop cube seems to be broken by the desktop wall configuration which puts the desktop viewports in a 2x2 square. And I can't turn it off. I unchecked "desktop wall", but that had no effect. Rather than a cube, I get a flat 3d plane. By dragging a window to the edge or quickly panning around, I can move left or right between the top viewports, however, I cannot access the bottom viewports in any way. Any idea what's going wrong?Hi, also if you run into anymore problems you can use this guide to setup the cube and effects, it has pictures for every step, so you can see what you are suppose to do as well as read it.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

