---
title: "Ubuntu 10.04 lucid lynx flashing boot screen help"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by scarzqc on 2010-05-18
Hi everybody !  I am a brand new Ubuntu user and i am using Ubuntu 10.04 lucid lynx.
I've been able to dual boot w/ windows seven but each time i am booting my ubuntu when the purple loading screen appears it starts to blink for a good 20 to 30 sec and sometimes it stucks there...  I've been looking around and i couldn't find any solutions this is why i am turning to you guys. Hopefully there is going to be a solution hehe :) 

F.Y.I :  my friend installed the same OS as me and he has the same flashing boot screen, could it be an error regarding ubuntu and not our pc's ?:(

---

### Post by QIII on 2010-05-18
Did you both use the same LiveCD to do your installations?

---

### Post by scarzqc on 2010-05-18
[COLOR=Red]> [/COLOR]Did you both  use the same LiveCD to do your installations?[COLOR=Red]

[COLOR=Black]we did not use any cd's, we went on the official ubuntu site and took it from there. we launched the exe and both been able to use ubuntu.[/COLOR]
[/COLOR]

---

### Post by sandyd on 2010-05-18
if you both have the same problem, its likely a problem with WUBI.
Follow the instructions on
[https://help.ubuntu.com/community/RecoveringWindows#The%20Windows%20Users%20Way%20of%20Resizing]("https://help.ubuntu.com/community/RecoveringWindows#The%20Windows%20Users%20Way%20of%20Resizing")
Then, Try installing a dual boot by booting up from the ubuntu livecd, and going to the "install ubuntu" menu option.
When you get to the partitioning stage, choose the option "use largest block of free space"


p.s. Uninstall ubuntu from the windows control panel first.
edit: what graphics card does you and your friend have?

---

### Post by QIII on 2010-05-18
In case you don't understand Carlee --

When we oldsters talk about a "dual boot", we are talking about a side-by-side, individual installation of both OSs completely independently of one another on different disk partitions.  That is entirely different from installing Ubuntu via Wubi.

It sounds like what you have done is a "Wubi" install, which does not install Ubuntu independently.  Briefly ...  You use the Wubi installer from within Windows.  This sets up what is known as a "loop device" on disk space reserved by Windows in your Windows partition.  You get to it via what is known as a "loop mount".  This arrangement allows Ubuntu to be run by hooking the Windows APIs.

That's all tech-geek-speak for "Ubuntu runs kinda like a program in Windows, but not exactly."

Wubi is really best used as a "test it out" solution, although many people use it on a permanent basis.

What Carlee is suggesting is an actual dual boot setup.

---

