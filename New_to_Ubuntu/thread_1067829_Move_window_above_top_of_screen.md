---
title: "Move window above top of screen"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-02-12
Is it possible to move the top of a window above the top of the screen??

What I mean is if I hold 'alt' and the left mouse button I can move my window down below the bottom of the phisical screen limits, but is there any way to do this with the top of the screen?

The reason I want this is becuase I am using an aspire one with a screen hight of 600 pixels, and I want to use a couple of packages that go beyond this hight.

I dont mind if I have to install aditional apps to achieve this or if can be done with a setting for a virtual screen size, but willing to look at any possibility.

---

### Post by hovzio on 2009-02-12
hi, are you running compiz? If you are it is done as follows. 

Press alt-f2 and type ccsm   (do you have compiz settings manager installed?)     Scroll to the bottom and find the "move windows" icon and click on it. There is an option "constrain Y"; uncheck this and you can pull the windows where you want. If you are useing "advanced desktop settings" and dont have compiz-config-settings installed open a terminal and digit;


sudo apt-get install compizconfig-settings-manager


hope this helps :)

---

### Post by Metallion on 2009-02-12
Thanks! I also needed this one actually. :)

---

### Post by celticbhoy on 2009-02-12
Just what I was lookin for.

Had it all installed and running, just wonder why it defaults to constrained ??

---

### Post by viktoria.s on 2011-04-22
Thank you for this advise! Just what I was needed too.

---

