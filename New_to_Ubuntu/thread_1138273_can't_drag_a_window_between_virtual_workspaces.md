---
title: "can't drag a window between virtual workspaces"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by dash86no on 2009-04-26
Evening all, 

I'm loving 9.04, very slick and everything is working just great. (except the webcam but the export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so trick I found on launchpad fixed that - go here if you experience a green screen on skype: 
[https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918))

One problem though: I can't seem to be able to drag windows between virtual workspaces. I can right click and select "move to workspace right" etc. but I can't perform the more intuitive method. 

Is this just me? They threw me off with the lack of "ctrl - alt - backspace" for a while so I though this is maybe another case of removing functionality in case it frightened away recent converts from windows. ("Oh my god, all my open programs have disappeared!!!)

Thanks,

Dash

---

### Post by danielpop on 2009-04-26
Unless you have Compiz enabled, it's not possible. A shame though, as Zenwalk, for example, lets you drag windows between workspaces without any effects enabled. Oh well...

---

### Post by Vunutus on 2009-04-26
Compiz is typically what handles this. If you enable compiz and it doesn't work by default, go into the options in CCSM for "Rotate Cube" and set "Rotate Flip Left" and "Rotate Flip Right" to the left and right edges of your screen, respectively.

---

### Post by jrothwell97 on 2009-04-26
It depends.

If compiz (Desktop Effects) is enabled, then you can drag a window to another workspace by dragging it to the edge of the screen. If you have simple-ccsm installed, you can enable Expo and map it to a key with System/Preferences/Keyboard Shortcuts.

If compiz is *disabled*, you can drag the window's taskbar button to the relevant workspace on the workspace pager.

---

### Post by dash86no on 2009-04-29
> **jrothwell97 said:**
> It depends.

If compiz (Desktop Effects) is enabled, then you can drag a window to another workspace by dragging it to the edge of the screen. If you have simple-ccsm installed, you can enable Expo and map it to a key with System/Preferences/Keyboard Shortcuts.

If compiz is *disabled*, you can drag the window's taskbar button to the relevant workspace on the workspace pager.

> **Vunutus said:**
> Compiz is typically what handles this. If you enable compiz and it doesn't work by default, go into the options in CCSM for "Rotate Cube" and set "Rotate Flip Left" and "Rotate Flip Right" to the left and right edges of your screen, respectively.

> **danielpop said:**
> Unless you have Compiz enabled, it's not possible. A shame though, as Zenwalk, for example, lets you drag windows between workspaces without any effects enabled. Oh well...

Thanks for the advice everybody.

---

### Post by holr on 2009-07-29
> **danielpop said:**
> Unless you have Compiz enabled, it's not possible. A shame though, as Zenwalk, for example, lets you drag windows between workspaces without any effects enabled. Oh well...

You could always try Brightside... just look for it in synaptic. It lets you custom configure screen corners etc without compiz.

---

### Post by locote on 2010-01-04
i had it and accidentally disabled it and just fixed it.  Go to **ccsm** and go to **rotate cube**, then click **bindings tab**, **rotate cube, rotate flip, click none and select the left side, then do the same for the right.**

---

### Post by ebug on 2010-04-24
This feature was a default before but now you need to activate it. If you are not using cube effect and only want to drag windows from one workspace to another, go to CompizConfig Setting Manager (CCSM) and enable Desktop Wall. Then, go to Edge Flipping tab and check Edge Flip Move. If you don't have CCSM, go to Ubuntu Software Center.

---

### Post by madone1 on 2010-05-06
> **ebug said:**
> This feature was a default before but now you need to activate it. If you are not using cube effect and only want to drag windows from one workspace to another, go to CompizConfig Setting Manager (CCSM) and enable Desktop Wall. Then, go to Edge Flipping tab and check Edge Flip Move. If you don't have CCSM, go to Ubuntu Software Center.

Thanks

---

### Post by darkscorpion20 on 2010-05-06
> **ebug said:**
> This feature was a default before but now you need to activate it. If you are not using cube effect and only want to drag windows from one workspace to another, go to CompizConfig Setting Manager (CCSM) and enable Desktop Wall. Then, go to Edge Flipping tab and check Edge Flip Move. If you don't have CCSM, go to Ubuntu Software Center.

Thanks, worked fine. I just changed to 10.04 from 9.10 and even though i had compiz affects on medium it still did not drag windows between.

---

### Post by - inferno - on 2010-05-07
> **locote said:**
> i had it and accidentally disabled it and just fixed it.  Go to **ccsm** and go to **rotate cube**, then click **bindings tab**, **rotate cube, rotate flip, click none and select the left side, then do the same for the right.**

[B]you can do it in desktop wall as well.......
go to Desktop Wall > Edge Flipping and enable it by clicking the checkbox.......
it solved the problem for me....:popcorn:[/B]

---

### Post by enigmatichus on 2010-05-22
Thank you so much!! It worked fine for me, too!! You saved me!!

---

### Post by xegroeg on 2010-06-05
In my case, I found that in CCSM in the 'Move Window' settings in window management, unchecking the 'Constrain Y' box free'ed my windows from being trapped on one monitor.

---

### Post by legendbb on 2010-09-28
Just add my experience here for uBuntu 10.04.1 desktop version.

Of course to get advanced desktop effect first, by installing "CompizConfig Settings Manager"

To enable Window Dragging in Desktop Wall, click Desktop Wall under Desk, click Edge Flipping Tab, and enable "Edge Flip Move" (which is not enabled by default).

:guitar:

---

### Post by geiroffenberg on 2011-04-12
Hi guys, i could suddenly not drag windows between workspaces. Tried the advice in this thread, but to no effect. Found out that in the appearance manager the "effects" had been set to none. I remember i had done it earlier to see if it enhanced performance on some audio apps i tried. 
So check the effects to normal, and the workspaces worked again.  So, there you go....

---

### Post by enigmatichus on 2011-04-12
I think you should check in System->Preferences->CompizConfig settings manager
There it should be a voice called "Desktop wall" or something similar (pardon my inaccuracy but I've got the italian version of ubuntu so I really don't know the english names of these tools and options)
Look if you may fix the problem checking this panel.

Luca

---

