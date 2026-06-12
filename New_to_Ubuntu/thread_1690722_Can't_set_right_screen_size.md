---
title: "Can't set right screen size"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by pierro504 on 2011-02-18
Hi,
I have just installed Ubuntu. It seems to be installed ok except that I can't see either the menu or task bar. I know the menu bar is there because I can open the menu by clicking outside of the screen area (and guessing where the menu is, I have another PC with ubuntu, so I know what it looks like).
 
So the screen is displayed larger than my actual monitor size.
I use a 42in TV as a monitor, connected via HDMI. Native resolution is 1920*1020, and it was detected correctly by Ubuntu.
When I change it through System/Preferences/Monitors, it changes the resolution but still does not show the menu and task bar.
 
How can I resize the screen so that I can see the bars?
Btw, Windows manages the screen fine (but blue screens all the time).
 
Thanks for your help.

---

### Post by Old *ix Geek on 2011-02-18
Have you tried shrinking the display using the monitor's controls? It sounds like it just needs a little adjustment.

---

### Post by pierro504 on 2011-02-18
Yes, I tried but this is a TV, and it does not seem to provide a way to shrink or expand the screen area. The only options are 16:9 (default), 4:3 (which truncates the sides), and 2 zoom options.

---

### Post by grahammechanical on 2011-02-19
What video card are you using. I have a Nvidia one and with the Nvidia driver installed I get a Nvidia X Server Settings utility on my Administration menu. With this utility is can select the GPU scaling from Stretched, Centered, Aspect Ratio Scaled. There is also a slider called Overscan Compensation. This is set to zero but I wonder, if I had your problem is this how I would fix it?

I cannot test out the Preferences>Monitors utility without disabling the Nvidia driver. And as I have things working just great I am not going to do that.

Regards.

---

### Post by pierro504 on 2011-02-19
I have a GeForce 8500 GT. I tried to intall the drivers but couldn't because of a more fundamental problem: wireless connection not working. It's connected to my wireless network, but internet  access isn't working. Anyway, I'll work on that one separately and will get back to this one asap.

---

### Post by pierro504 on 2011-02-21
I installed the Nvidia driver, then changed the resolution to 1600x1024 instead of native 1920x1080. This does not cover the entire screen but at least I can see the menu and task bars.
I played with the scaling but couldn't get it to cover the whole screen while still showing the menus.
Anyway, thanks for your help, much appreciated!
Pierre

---

