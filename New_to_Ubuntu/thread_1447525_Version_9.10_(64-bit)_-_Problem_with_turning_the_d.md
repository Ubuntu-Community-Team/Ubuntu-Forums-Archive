---
title: "Version 9.10 (64-bit) - Problem with turning the display off using xset"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by max92 on 2010-04-05
Hi, 

I am running Ubuntu version 9.10, 64-bit on a lenovo SL410 laptop. I would like the option to turn off the display in order to conserve power when it isn't required, such as while downloading files or listening to music.

After looking around a bit, I found a command,

```
xset dpms force off
```which does turn off the screen. However, after some time (1-2 minutes), the display would turn back on even if I don't press a key or move the mouse.

Thus, my question is:

a) Does anyone know, or have any suggestions on what is causing the display to turn back on? 

b) And if not, is there another way to achieve this without using xset?

Thank you in advance for the help.

-Max

---

### Post by gordintoronto on 2010-04-05
Have a look at your computer manual. On many laptops, there is a key combination which will turn off the screen, such as Fn-F2 or Fn-F4. Actually, it doesn't so much turn off the screen as cycle among built-in screen, VGA port, both.

---

### Post by max92 on 2010-04-05
> **gordintoronto said:**
> Have a look at your computer manual. On many laptops, there is a key combination which will turn off the screen, such as Fn-F2 or Fn-F4. Actually, it doesn't so much turn off the screen as cycle among built-in screen, VGA port, both.

Actually, that's the first thing I tried (forgot to mention that #-o). I also grabbed the tpb package from Synaptic, but I doubt it's up to date / compatible with this model / being used correctly by me.

Nevertheless, I'll go grab the computer manual and give it a read again.

---

