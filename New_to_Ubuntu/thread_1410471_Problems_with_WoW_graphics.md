---
title: "Problems with WoW graphics"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by tsuchang on 2010-02-18
I'm a World of Warcraft player.  This week I have been having problems with the graphics in the game.  most areas of scenery are showing as white.  Some areas are normal, like in buildings and in towns and cities but the country areas the ground is white with some plants showing.  I have put my video settings to minimal and that doesn't fix it.  I did the "world of warcraft repair" thing but that didn't fix it.  I had this problem when I was using something other than Ubuntu during the WoW beta and fixed it by changing some code.  I got that fix from a forum but that was years ago and I have no idea how to fix it now.  I updated my video card driver as well
Thanks.

---

### Post by Satoru-san on 2010-02-18
What brand and type of card do you have?

if it is ATI, make sure you are using the restricted drivers, if they work with your card, as the free drivers render some things wrong, in my experience.

---

### Post by tsuchang on 2010-02-22
solved it.
I found this article.
OpenGL or Direct3D

Background

The Windows version of World of Warcraft supports rendering using either Direct3D mode (the default) or OpenGL mode (it can be configured to use OpenGL). On Windows, most people just use the Direct3D mode, as it is the most tested and it has a number of features over the OpenGL mode, such as support for a hardware cursor. In wine, Direct3D is supported only through an emulation layer (known as WineD3D), that runs on top of OpenGL. At the moment, WineD3D lowers the fps enough that most people running WoW using wine tend to use the OpenGL mode instead.

WoW can be set to use its OpenGL mode as follows:

Find the file wtf/Config.wtf in your main WoW directory. By default it is found in /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/, where <username> is you computer login name. Note that since .wine begins with a period, you will not be able to see it, but you may still access it in a terminal. In the Nautilus file manager, you can press Ctrl + h to see hidden files. If config.wtf does not exist, run the game and log into a character, then exit WoW. The game should then have created the file. Open it using a text editor, and add the following line to it:
SET gxApi "opengl"

---

