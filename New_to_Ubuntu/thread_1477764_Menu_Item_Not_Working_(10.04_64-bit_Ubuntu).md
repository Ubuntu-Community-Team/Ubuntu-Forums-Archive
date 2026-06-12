---
title: "Menu Item Not Working (10.04 64-bit Ubuntu)"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-05-09
Ok, thought I would post and see if I'm just stupid or what... 

I'm trying to make a menu item for Gish, so I right clicked on the menu and went to edit menus. Then I navigated to where I wanted it, put the information:

Type: Application
Name: Gish
Command: /home/user/gish153/gish64

When I try to open it, the box that comes up, instead of showing the game, it is a grey box with a white box wherever the mouse would be. So, I navigated to the folder through nautilus, double-clicked gish64 and it ran just fine... Any ideas what the problem could be?

---

### Post by Ozymandias_117 on 2010-05-10
Bumpity Bump Bump

---

### Post by dtfinch on 2010-05-10
In the past, for some programs, I've had to make a shell script that would cd to the directory of a program before running it. Then I'd mark the shell script as executable and point the launcher to it.

There's a note at the bottom of [http://www.chroniclogic.com/gish_download.htm](http://www.chroniclogic.com/gish_download.htm) saying the same.
"Gish also must be run in X from the actual folder its installed in"

#!/bin/sh
cd /home/user/gish153/
./gish64

---

### Post by Ozymandias_117 on 2010-05-10
Oops :D thanks :P I downloaded it from the Humble Indie Bundle thing and never thought to check their site...

---

