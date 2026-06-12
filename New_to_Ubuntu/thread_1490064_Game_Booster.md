---
title: "Game Booster?"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by Feyerbrand on 2010-05-21
I have the HP mini 311 with ubuntu 10.04 newly installed.  I am fresh to the ubuntu world, but I do have compiz installed and the mac4lin theme with docky on the bottom.  I am using Wine to run the games including starcraft Broodwar and it runs really choppy.  Where before I switched to ubuntu windows 7 ran starcraft, and world of warcraft at amazing speed.  I was wondering if there is a way to turn off effects from the desktop when running a full screen application so that way it gets more power to the processor.  I used Game Booster by IO Bit and that ran wonders on the laptop.  

System Specs

Intel Atom - 1.67 GHZ
Nvidia Ion
3 GB Ram
320 GB HDD

---

### Post by -humanaut- on 2010-05-21
The only way I can think of feasible turning off effect would be write a bash script that you launch with the game. I don't know though there maybe someway to do it with wine.

---

### Post by Feyerbrand on 2010-05-21
> **-humanaut- said:**
> The only way I can think of feasible turning off effect would be write a bash script that you launch with the game. I don't know though there maybe someway to do it with wine.do you know of any easy bash script that i could make a button for on the desktop or something for running games?  so when I turn the game off I can switch back to normal mode?

---

### Post by -humanaut- on 2010-05-21
I'd try googling for one I'm sure something exist out there that would be easy to implement but I'm not sure try google if you can't find anything Ill help you write a bash script.

---

### Post by Feyerbrand on 2010-05-21
I have actually scoured the internet and tried out two or three bashes that are either 

1- to have an on and off when running an app but running terminal and typing in the   name of the script and then the title of the game


2-an auto on and off of all features with a click of a desktop icon.  

The issue I had is when I followed the instruction it froze my laptop disabled half of the main functions of the os and I had to reboot the laptop.  After the laptop reboots the system runs perfect again.  I was hoping someone had already made a program for it.  I know that many computer nerds like myself a huge gamers and I don't want to have to be tethered to my quad core desktop all the time for lan parties

---

### Post by -humanaut- on 2010-05-21
You could setup another user-account with all the effects disabled and just use it for gaming. Thatd be the simplest solution

---

### Post by yoreei on 2012-09-03
I know this is an old thread but there IS actually a solution to your problem. Ubuntu generally uses less resources than Windows 7 does even with Gamebooster on. Still running games with Wine is way choppier so the problem isn't in the background processes but actually in Wine itself. 
Most of the games for Windows are made with DirectX. This DirectX thing runs only on Windows so its wine's job to emulate it. Here lyes your problem. Running DirectX on Wine is choppier because things are not well optimized.

The solution:

Some games (especially those that run on Mac too) support not only DirectX but OpenGL.
(Because its Mac's alternative to DirectX). The good thing is that OpenGL runs natively on Linux (not like DirectX) and those games that support it can usually be set (in the game's settings or some config files) to use OpenGL instead of DirectX which result's in  better performance.

So, let me give you a real world example.

Today I installed World of Warcraft on my Xubuntu 12. The first time I played it, it ran really choppy. It was later when I remembered that WoW runs on DirectX by default so I added the line 
SET gxApi "opengl"

to WTF/config.wtf and the next time I ran the game, the 
performance was similar to the one I had with Windows before 
I switched to Linux (As a head-up I think that it might be 
even better but as it was long time ago I am not completely 
sure). The only downside I got with this change is that some
of the Video options are not available and automatically set to
lowest. Those are:
Shadow quality
Liquid Detail
Sunshafts
Ground clutter (with the exception that the max here is fair, 
not low). 
Everything other is maxed and the game is running smoothly. As
a conclusion switching to OpenGL is worth it!

[IMG]http://img152.imageshack.us/img152/4844/wowopengl.jpg[/IMG]

If switching to OpenGL doesn't bring the performance to 
a Windows-like level, then you should check if you have installed
the binary blob for your graphics card (this means - the driver)
Some Linux distros don't install it automatically because the
drivers for all of the famous graphic cards are closed source
which is against Linux's philosophy. You should either check
Additional Drivers on Ubuntu or find and install the compiler
manually from the manufacturer's website.

At last, if all of the above methods can't help you and you are
sure it is the operating system's resource usage, then you should
find a lighter alternative for the applications that your 
system uses.
For example, switching to OpenBox and LXDE can free up some 
precious RAM
Thunar is a file manager which is famous for its lightness.

You can also clean up your system with the following tools
Bleachbit - cache and temporary files
GConf Cleaner - unused registry stuff

Reducing the swappiness is also a good practise

```

gksudo gedit /etc/sysctl.conf

```Then find the line:

```
vm.swappiness=SomeValueHere
```and change it to

```
vm.swappiness=10
```Be free to experiment with values from 0 to 100. The best option
will vary depending on how much RAM you have but 10 is good for
most configurations as written here:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

While I was searching for more ways to improve game performance
on Linux I found this old and rusty thread and I thought that
I should give an appropriate answer to it as such there was not.

That's all folks! :D

External Links:
[https://en.wikipedia.org/wiki/DirectX](https://en.wikipedia.org/wiki/DirectX)
[https://en.wikipedia.org/wiki/OpenGL](https://en.wikipedia.org/wiki/OpenGL)
[https://en.wikipedia.org/wiki/Binary_blob](https://en.wikipedia.org/wiki/Binary_blob)
[https://en.wikipedia.org/wiki/Swappiness](https://en.wikipedia.org/wiki/Swappiness)
[https://en.wikipedia.org/wiki/Lxde](https://en.wikipedia.org/wiki/Lxde)
[https://en.wikipedia.org/wiki/Openbox](https://en.wikipedia.org/wiki/Openbox)
[https://en.wikipedia.org/wiki/Thunar](https://en.wikipedia.org/wiki/Thunar)
[https://en.wikipedia.org/wiki/BleachBit](https://en.wikipedia.org/wiki/BleachBit)
[http://www.ghacks.net/2010/09/21/clean-up-gconf-database-with-gconf-cleaner/](http://www.ghacks.net/2010/09/21/clean-up-gconf-database-with-gconf-cleaner/)

---

