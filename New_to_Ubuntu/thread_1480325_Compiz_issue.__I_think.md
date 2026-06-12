---
title: "Compiz issue.  I think?"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by jd342 on 2010-05-11
So this is I think my third time installing Ubuntu over the past few years.  It's never stuck for one small reason or another, but I'm really liking it now, and I'm actually motivated to get my problems resolved.

Either way, I'm running the 64 bit version of Ubuntu 10.04.  Everything installed fine, but I knew nothing about Compiz/Metacity/Emerald (still don't really) when initially configuring some settings, and I think I may have screwed something up somewhere along the way.  This may be something simple that has already been discussed, so I apologize if I'm restating a common problem, but I haven't been able to find an issue with similar symptoms.  I had Compiz and Emerald installed, although I'm not really sure how I did those.  After some of the stuff came up, I removed Emerald, and things were a little better temporarily, but most of the issues came back up.

Ok... so the first thing I noticed was that when I have a screen saver up, and I move the mouse to get the login prompt, the screen saver stop, but doesn't go away.  After a few minutes of trying to get the password screen, I figured out that the prompt is there, I just can't see it.  So typing in the password and pressing enter worked.  But that still doesn't seem right.

(and I just remembered something else that may or may not play into everything.. I can't get the color of the cursor to change.  I changed the settings in the Preferences > Appearance screen, but the color doesn't change on the desktop.  But it will if I'm running another program.)

The screen saver thing is annoying, but what happened next forces me to restart.  After configuring compiz, I can get the Desktop Cube to work.  But I was looking at some of the other effects, the rain and fire ones I think, and pressing the commands to see what they do (shift f9 for example) causes the bar with the minimize and maximize buttons to stop working.  I can drag the windows, but the bar itself goes either completely black, or shaded.  And windows for applications other than firefox turn this color entirely.  So opening a window to launch the terminal will open a completely black, unresponsive window.  Since nothing works, I have to restart, which does fix it.

I was searching the forums to find a fix, and one suggestion was to have a startup command that launches compiz.  I did this, and it seems to have made matters worse as I can't even use the desktop cube now.

This is obviously frustrating, but I'm just looking for a solution that doesn't require a complete OS re-install.  Is there a way to set just Compiz/Metacity/Emerald back to their default settings?  And when that's done, how do I change the settings without breaking anything?

Again, sorry if I'm going over something that's already been discussed.  And sorry if this is all basic stuff.. I'm still trying to get used to something that's not Windows.


In case it matters, here's my hardware configuration:

Intel Core 2 Duo 3.0 ghz
XFX Radeon HD 4870 (the drivers for this were installed as that was one of the first things that came up after the OS installation)

Thanks!!

---

### Post by warfacegod on 2010-05-11
Go into your Home folder and hit Ctrl+H. That will show you hidden files and folders. Scroll down until you see .compiz, deleting this folder should set everything back to default.

You may want to get simple-ccsm from Synaptic. Its not overwhelming like the CompizConfig Settings Manager can be.

---

### Post by themusicalduck on 2010-05-11
If you go to System > Preferences > Screensaver - you can disable the password login prompt from there, assuming you don't mind the PC not being locked when the screensaver is on.

---

### Post by jd342 on 2010-05-11
Deleting the compiz file didn't work.  And I think I made it worse  by  completely removing compiz from the Synaptic Package Monitor.  Now when I  restart, it's not using metacity as my window manager, and since  there's no window manager, the title bar is completely gone.  I can get  it to come back by opening a terminal and using the "metacity --replace"  command, but it goes away on the next restart.  

Also, when I close the terminal, I'm not able to enter text..  The terminal flashes a hollow box instead of a solid one, and the keyboard doesn't work for any applications.

Pretty sure I screwed something up here.  I could just install compiz again, but I want to get metacity working right, AND figure out why compiz wasn't working the first time.

As for the screen saver... yeah, I could do that.  But I'd rather find out what's wrong and fix it instead of just ignoring the problem.

But hey, the cursor is finally black!  At least something is working.

---

### Post by warfacegod on 2010-05-11
```
sudo apt-get purge compizconfig-settings-manager
```

Then:

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by adam22 on 2010-05-11
I would honestly just reinstall. It takes about 15 minutes....faster than troubleshooting this mess.

Emerald isn't worth it in my opinion, it's just a pain in the *** theme manager, and if you use Compiz and Emerald, you're replacing the default window and theme managers, which presents problems if you try to revert back.

Anyways, CCSM isn't confusing...I made a guide about using Compiz. Check it out [here](http://ubuntuforums.org/showthread.php?t=1414548).

---

### Post by jd342 on 2010-05-11
Reinstalling compiz has everything usable again, but I'm still having the same problems as before..  It's minor stuff really, but it still kind of bugs me.  Like the pointer.  When I'm in an application, Firefox for example, it's black like the one I selected.  But anywhere on the desktop it's white.  And when I try to toggle the water effect from the compiz settings screen, obviously not a huge deal, instead of seeing rain, everything goes either black or a faded gray.  And there's the screen saver thing also.  I'm probably just going to reinstall 10.04 at this point and see if that works.

---

### Post by warfacegod on 2010-05-11
Did you go to System> Admin.> Hardware Drivers and activate the Recommended driver for your video card?

---

### Post by adam22 on 2010-05-11
Open source driver or ATI driver?

---

### Post by jd342 on 2010-05-11
Yeah the recommended driver is activated.  It's the proprietary ATI driver

---

