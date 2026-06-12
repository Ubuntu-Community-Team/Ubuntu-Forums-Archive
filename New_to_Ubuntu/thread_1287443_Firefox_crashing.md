---
title: "Firefox crashing"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-10
I think I botched up my Firefox install by getting confused with the whole 3.5/Shiretoko thing, completely removing, then installing again.

Now Firefox seems to crash once or twice a day (using only V3.08).

Would you experts reccommend completely removing again and installing again, or just sitting still and seeing what happens? I can sort of live with the latter for a while.

I'm just trying out Ubuntu just for the hell of it.

It crashed once on Youtube today (without even selcting/viewing a video) and maybe once on Facebook.

When it crashes, the whole system seems to freeze and I can't even move the mouse. Is there a CTRL+ALT+DEL/Task Manager thingy in Ubuntu? One which I don't need to go thru the menu or anything?

---

### Post by diablo75 on 2009-10-10
I did something similar with my computer.

I managed to get it fixed by uninstalling firefox completely and then reinstalling it using apt-get in the terminal window.  Synaptic Package Manager didn't seem to display all the packages related to it so you might do the following:

First, open up System>Administrator>Software Sources>Third Party (tab) and uncheck any sources that are associated with Firefox 3.5.


Next, open a terminal and type:

```
sudo apt-get remove firefox(press the tab-key here three times)
```

Pressing the tab-key in terminal usually auto completes things for you if what you've typed so far is completely unique the rest of the way.  But if it's not unique, pressing the tab key three times will make the terminal output a list of possibilities you could complete the command with.  All you will need to remove is the "firefox" package, as well as the "firefox-3.5" (I think that's what it might look like).  Or something like that.

Once the software is removed, do a:

```
sudo apt-get update  && sudo apt-get install firefox
```

I'm not on the computer I did this to at the moment so I might be wrong on the exact package name, but it should be close...

---

### Post by lovinglinux on 2009-10-10
[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by penguintutor on 2009-10-10
Best way to fix is normally to remove and reinstall fully using the package manager. Assuming you haven't added another repository this should be straight-forward using diablo75 instruction, or by using Synaptic Package Manager. 

I have 3.5 installed alongside the package installed 3.0 without any problems. I did this by downloading the binaries from Mozilla which is supplied as a .tar.bz file rather than a .deb file (ubuntu package). 

Follow the instructions for installing, but when it asks for which directory to install to choose /opt/firefox (or something similar). I then left the existing launch icons, but added a new one to the top panel which linked to the program /opt/firefox/firefox

If I want to launch 3.0 then I use the original icons, but normally I just click on the new icon to launch 3.5.

This means that when Karmic is released I can safely choose upgrade and just remove the icon and /opt/firefox directory to revert to the official package.

---

