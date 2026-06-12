---
title: "Graphic driver for intel 855GM chipset"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by dronubu on 2011-05-06
I have Dell Inspiron 700m with intel 855GN chipset. I have problem on mine Ubuntu 11.04 i can't lunch Unity because i don't have driver installed. I found 3D driver on [http://intellinuxgraphics.org/2011Q1.html](http://intellinuxgraphics.org/2011Q1.html) but i don't know how to install. Help me please with this issue.

---

### Post by Rubi1200 on 2011-05-06
Hi and welcome to the forums :-)

You need to understand some things and consider them carefully before attempting what you want to do.

First, if you do this the chances of breaking your system are quite high.

Second, from what I have read, you are also installing packages that are not directly part of the kernel and as such you may find yourself in a situation where, even if it works, that you will not receive security and other updates for your installation.

Third, you are compiling from source and there will probably be a lot of tweaking required afterwards, some of which may work and some not (see my first point again).

Finally, according to Stefan Glasenhardt, who packaged a fix for this chipset for 10.04 and 10.10, this card does NOT work on 11.04 PERIOD. He says it might, and I stress again, might work with Mesa but this has not been tested.

So, what are your options?

1. try installing the driver you found:
[http://intellinuxgraphics.org/build.html](http://intellinuxgraphics.org/build.html)

2. try installing Unity 2D:
[https://launchpad.net/ubuntu/+source/unity-2d](https://launchpad.net/ubuntu/+source/unity-2d)
I haven't tried this, but I believe it is now available in the official repositories

3. use the Classic desktop option from the login screen instead. It's not Unity, but at least you will have 11.04 on the computer

4. no disrespect intended, consider buying a newer computer capable of handling Unity. Here are the hardware requirements:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

Last, but not, least I urge you to test these things in something like VirtualBox first before you do it on the actual machine. If something goes wrong, you just delete the virtual machine and start again.

---

