---
title: "Compiz problem."
date: 2010-05-09
forum: New to Ubuntu
---

### Post by bob brazie on 2010-05-09
Clean install of Ubuntu 10.04.

This is the terminal out put when i try to run Compiz.

bob@bob-laptop:~$ compiz
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

---

### Post by themusicalduck on 2010-05-09
What graphics card do you have? and have you installed proprietry drivers for it?

When running compiz from the terminal, you use ```
compiz --replace
``` rather than just "compiz". But if you set it to on from System > Preferences > Appearance > Visual Effects does it not run and run on startup?

---

### Post by tom.swartz07 on 2010-05-09
I get the same warning too; it doesnt seem to be anything to worry about.

if you really want to check if compiz works on your computer, try running this program i have attached. it will run all of the tests you need for compiz.

---

### Post by bob brazie on 2010-05-10
Compis is an application to help set differant effects in Ubuntu is it not?

Maybe I am thinking it is something it is no. <g>

---

### Post by themusicalduck on 2010-05-10
Ahh, so you want to change the settings for the desktop effects? Compiz in itself is a window manager, and it is the program that provides the effects you see.

If you want to change the settings for compiz, then you need to install two programs. If you search for ccsm in the Software Centre, there should be two programs, Advanced Desktop Effects Settings and Simple CompizConfig Settings Manager. Install them both and then look for CompizConfig Settings Manager under System > Preferences. Or for a simpler less powerful configuration menu, use Simple CompizConfig Settings Manager.

---

### Post by bob brazie on 2010-05-10
Well, that takes care of that!! <g>

Thanks, that is the utility I was looking for and you showed me the way.

---

