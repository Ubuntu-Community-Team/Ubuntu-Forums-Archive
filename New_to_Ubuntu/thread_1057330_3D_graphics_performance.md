---
title: "3D graphics performance"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by David R. Ingham on 2009-02-01
I have a Diamond ATI Radeon 4650 card on a Gateway desktop PC.  I use this for Second Life virtual reality, which is 3D graphics intensive.  Accepting an instalation suggestion that popped up on the Ubuntu desk top did not enable the 3D graphics features, so I ran ATI's Driver Installer 9.1.  It works now except that I only get about half the 3D frame rate that I did with µ Soft Windows (around 15 fps, instead of 30).  I don't know if this is Ubuntu's, ATI's or Second Life's fault.  Must I go back to Windows?
There are other problems, but this is currently the only one that I can't live with or work around.

---

### Post by David R. Ingham on 2009-02-02
Perhaps what I need is a version of Linux without a (Xerox style) graphical user interface? (It doesn't really work anyway, because Firefox doesn't run in a window.)  Things happen, like the screen flashing black and the graphics mode depending on the history, that suggest that Ubutu's user interface is interfering with the graphics.
I think this is the right forum to post this, because it seems to be about the suitability of Ubuntu for particular uses, so it should be considered early on.

---

### Post by sydbat on 2009-02-02
Do you have desktop effects (compiz) turned on? If so, that might be the entire problem.

To turn off desktop effects go to System > Preferences > Appearance > Visual Effects tab > choose None.

If that works, you will probably have to play your game with this setting off, then turn it back on after.

Personally, while I like the whole cube idea (among other things), I find it interferes with graphic intensive apps, so I leave it off...unless I am impressing friends with the whole "gee isn't this cool" thing...

---

### Post by David R. Ingham on 2009-02-02
Thanks Sydbat, that sounds like to right way.  Secondlife has a higher frame rate but at 640x480 pixels!  It quits when I uncheck "Run in a window" and even after going back to "normal" desktop in "Preferences" I can't select any higher screen resolution.  The window resolution window won't close.  I will try re-booting, but last time I tried that I had to re-install Ubuntu and lost my Windows partition.

---

### Post by GeneralCody on 2009-02-02
> **David R. Ingham said:**
> I have a Diamond ATI Radeon 4650 card on a Gateway desktop PC.  I use this for Second Life virtual reality, which is 3D graphics intensive.  Accepting an instalation suggestion that popped up on the Ubuntu desk top did not enable the 3D graphics features, so I ran ATI's Driver Installer 9.1.  It works now except that I only get about half the 3D frame rate that I did with µ Soft Windows (around 15 fps, instead of 30).  I don't know if this is Ubuntu's, ATI's or Second Life's fault.  Must I go back to Windows?
There are other problems, but this is currently the only one that I can't live with or work around.

Well, I don't think it's anyones fault but your own!
If you download the latest drivers from ATI, and use the updated Xorg distribution, things should work just nice and dandy. What does the glxgears give you?

---

### Post by David R. Ingham on 2009-02-02
Ok, after re-boot and some fiddling with the preference pains and the application program, I have the screen resolution under control and the graphics working right, in window or full screen.  Performance seems about like it was on µS. Windows now.  I can always switch to my Mac when I want fancy effects.
Thanks again, Sydbat.

---

### Post by David R. Ingham on 2009-02-09
Whoever is working on the desktop software might think about making the effects automatically turn off if a window is maximized or the computer goes in full screen mode.

---

### Post by Gannon8 on 2009-02-09
1. What game is it?
2. Is it a linux game or a windows game installed with WINE?

I am not sure what the speed difference is between running an .exe on windows or with wine, but one of my games gets an unacceptable framerate on ubuntu (only reason I still have windows)

---

### Post by unplugged23 on 2009-02-09
> **Gannon8 said:**
> 1. What game is it?
2. Is it a linux game or a windows game installed with WINE?

I am not sure what the speed difference is between running an .exe on windows or with wine, but one of my games gets an unacceptable framerate on ubuntu (only reason I still have windows)

Yes, anything being emulated to run on something other than a native OS will always be a little laggy.

---

### Post by Paqman on 2009-02-09
> **David R. Ingham said:**
> Whoever is working on the desktop software might think about making the effects automatically turn off if a window is maximized or the computer goes in full screen mode.

Not abad idea. I certainly think it'd be worth having Compiz switch off during fullscreen video playback.

---

### Post by David R. Ingham on 2009-02-10
This is Second Life virtual reality.  I am using a Linux (beta) version.

---

