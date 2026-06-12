---
title: "Nividia Problems"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by evil_urna on 2009-06-09
I have a nvidia FX 5500, laugh it up, and I am running 9.04. I was trying to run a game on wine and it was chugging along really badly so I thought I might have a driver issue so I tried installing the 173.14.18 driver.

err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter

and now I get this error when I try to start any game. I was getting an error about a mismatching nvidia kernel but I tried reinstalling the driver for something like a third time and I no longer get that error. What problem might I have?

---

### Post by prvteprts on 2009-06-09
I also have a FX5500 lol. What game is it? Maybe the FX5500 is way too outdated for it.

On the other hand, I was only able to install 173.14.16. I couldn't get 173.14.18 to work - X won't start if I use it. You could try

sudo apt-get remove --purge nvidia-glx-173 

to uninstall the driver, and then make a fresh reinstallation.

---

### Post by evil_urna on 2009-06-09
> **prvteprts said:**
> I also have a FX5500 lol. What game is it? Maybe the FX5500 is way too outdated for it.

On the other hand, I was only able to install 173.14.16. I couldn't get 173.14.18 to work - X won't start if I use it. You could try

sudo apt-get remove --purge nvidia-glx-173 

to uninstall the driver, and then make a fresh reinstallation.

ok I installed that 16 driver and I no longer have x failures on startup. And the game will boot but it runs very slowly. 

I am trying to play the first red faction game and I know it works with this hardware, on windows anyway.

---

### Post by prvteprts on 2009-06-11
Are you running the game under WINE?

---

