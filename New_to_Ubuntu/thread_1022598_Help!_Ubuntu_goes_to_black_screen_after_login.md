---
title: "Help! Ubuntu goes to black screen after login"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Jonathan Brennecke on 2008-12-27
I'm fairly experienced with computers as far as mac and PC, but I'm entirely new to linux... as in, installed it yesterday sort of new. 

I had everything working perfectly with Ubuntu on my Dell inspiron B130 (1GB of RAM, Celeron @ 1.6GHz)until suddenly I log in... everything seemed normal at first, my desktop background appeared as usual, and then suddenly the screen went black with strange, purple lines where the bottom and top panel taskbars should be. I've tried everything that came to mind, short of reinstalling the OS, but to no avail.

I have access to terminal from the login screen, but honestly, I don't know my way around a linux command line interface yet. I don't have access to anything else (such as GNOME) I don't think...

My hunch is that the problem may have had something to do with compiz, which I was just installing and setting up when all this went awry. I suppose there is some way to disable compiz from the terminal, but I wouldn't know how.

Any help is greatly appreciated, thanks in advance.

EDIT: Oh, and MERRY CHRISTMAS!

---

### Post by lykwydchykyn on 2008-12-27
When you boot, do you get the graphical login screen, or only the text?
Or does it go black after logging in?

---

### Post by Jonathan Brennecke on 2008-12-27
When I boot it goes to the graphical boot screen as usual. In fact, everything seems normal... I enter the username and password, it goes to the normal brown loading screen, even the typical desktop background appears...


then my world goes black :(

---

### Post by lykwydchykyn on 2008-12-27
Try logging in again, but this time change the session to "failsafe".  That should get you to a single terminal session, but running in a GUI, not a text console (not sure if my terminology makes sense there...)

You can launch your config tool from there and disable effects.  I'm not sure what the command is (not a GNOME user), but maybe someone else here can help.

---

### Post by Thameslink on 2008-12-27
esc to enter the grub menu and use safe mode (or recovery mode) for the kernel you want boot.

If you've already got it to boot to the desktop once and now, following an update it wont work. You need to repair the x console, either via the grub menu, or live cd I forgot which. One desktop I have wont work with the ATI proprietary drivers which it installs at update.

It may help if you specified what graphics card & monitor you are using

Cheers

---

