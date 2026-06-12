---
title: "xorg cpu / metacity won't restart"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by goodbyemrevans on 2011-05-25
whenever I play the battle for wesnoth, after a little while (I haven't timed it but maybe 30-45 minutes) xorg starts to use up more and more of the cpu, making it unplayable.  quitting the game doesn't stop this.  killing metacity through top does, but then I don't have a window manager.  restarting with ```
ctrl+alt+backspace
``` doesn't do anything, and when i run ```
metacity --replace
``` or the same with a different window manager, the display changes a bit but the process in the terminal never ends.  what should i do?

ubuntu 10.10 netbook remix, ubuntu netbook 2d, asus 1015pe eeepc, usb boot drive install

---

### Post by goodbyemrevans on 2011-05-25
My workaround for this problem seems really ugly - killing the window manager then leaving an eternal terminal process to languish on another workspace.  A lot of people seem to have or have had a problem like this with xorg, but there are very few solutions.  The most definitive-sounding was to check my graphics drivers, but that doesn't seem to be the issue, since none are proprietary.  Another suggested start killing processes and see which one gives back the CPU - that seems to be metacity, but I don't know what to do from there.  I want to stop this problem from recurring, rather than patching it with duct tape.

---

