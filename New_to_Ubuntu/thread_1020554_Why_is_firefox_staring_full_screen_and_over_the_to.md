---
title: "Why is firefox staring full screen and over the top panel"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by geekyhawkes on 2008-12-24
Hi

for some reason my firefox has now started to launch in a pseudo full screen mode.  It launches and covers the top panel, but if i hit F11 (full screen) and then click maximise it resizes and the top panel becomes visible again.  This is more of an annoyance than anything, but i dont understand why this has changed.  

Any ideas of a fix?  

(Im running 8.10 and do use compiz if that changes anything)

---

### Post by frank002 on 2008-12-24
I have had that problem intermittently also. Since latest update it has not occurred any more.

---

### Post by balaknair on 2008-12-24
A fix: Unmaximize and resize the Firefox window so that it fits within the top and bottom panels. Close Firefox. Now when you start firefox again, the window will fit on the screen.

---

### Post by LowSky on 2008-12-24
Its actually a compiz/firefox/nvidia problem... mostly nvidia's latest driver. Nvidias latest beta makes the issue go away, but it isn't stable so just press F11 if the FF3 window goes fullscreeen again.

---

### Post by teh_yodeler on 2008-12-24
> **balaknair said:**
> A fix: Unmaximize and resize the Firefox window so that it fits within the top and bottom panels. Close Firefox. Now when you start firefox again, the window will fit on the screen.

I had this problem for a while.  Then I did what's in the above post here.  It was bugging me for days and all I had to do was resize the firefox window to fit and then close it.  Since then I've had no problems.

:)

---

### Post by malleus74 on 2008-12-24
I can tell you from experience it affects ATI cards, too. I ended up deleting all the firefox settings since it just wouldn't resize for me. I had to leave a nautilus window up maximized so I could tab back and forth.

---

### Post by stanz on 2008-12-24
same here...compiz/firefox/nvidia - had me spending more time figuring out things and searching, then doing what I needed to do.
It's un-installed for now.

---

### Post by BGFG on 2008-12-24
I had the same problem. In my case after a little research, the resolution was turning off effects via system>>preferences>>appearance>>visual effects: set to none.
But updates ( i don't know which) fixed it.

---

### Post by wsonar on 2008-12-24
Yes this is clearly a bug Fire Fox 3.0.5 this broke on my profile not sure what caused it, but now the bar is above the screen and if I do alt space and try resize or move window they do nothing

I've messed with the compiz settings but still not working works if I log in as a diffrent user

none the less pretty annoying

---

### Post by wsonar on 2008-12-24
> **teh_yodeler said:**
> I had this problem for a while.  Then I did what's in the above post here.  It was bugging me for days and all I had to do was resize the firefox window to fit and then close it.  Since then I've had no problems.

:)


Resize and move have no effect even after choosing unmaximize

---

### Post by kansasnoob on 2008-12-24
I had so much trouble after recent Firefox updates I decided to try Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/?f=print](http://ubuntuzilla.wiki.sourceforge.net/?f=print)

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

Very, very happy so far with Ubuntuzilla on Intrepid. Only somewhat happy on Mint 6:

[http://ubuntuforums.org/showthread.php?t=1016213](http://ubuntuforums.org/showthread.php?t=1016213)

But I have some follow up to do there!

---

### Post by wsonar on 2008-12-24
I installed the latest version of opera it's pretty light and I like it

---

### Post by balaknair on 2008-12-25
If you can't see the edges of the window to resize, hit alt-F8 to resize.

This is indeed a bug with nVidia-Compiz-Firefox, supposedly fixed in the latest nVidia drivers(177.82). Resizing the window is only a temporary workaround.

---

### Post by niemaodpowiedzi on 2008-12-25
> **BGFG said:**
> I had the same problem. In my case after a little research, the resolution was turning off effects via system>>preferences>>appearance>>visual effects: set to none.
But updates ( i don't know which) fixed it.

This worked for mine, at least temporarily. I have a fresh install of Ubuntu (as in, since yesterday) and this bug popped up tonight and was driving me batty.

---

### Post by BGFG on 2008-12-25
> **niemaodpowiedzi said:**
> This worked for mine, at least temporarily. I have a fresh install of Ubuntu (as in, since yesterday) and this bug popped up tonight and was driving me batty.

Open a terminal, type 
```

sudo apt-get update

```

hopefully this will get you all the updates needed to resolve this problem. My machine is AMD/nvidia based, 64 bit.

---

### Post by DigitaLink on 2008-12-26
I'm not using nVidia anything, and this bug just cropped up tonight.  Annoying as heck.  Can't even unmaximize.  Can't resize.  Can't move the window.  Irritating in the extreme.

EDIT: I just used Synaptic to do a complete removal and re-installation.  Fixed the problem.  Remember that removing firefox also removes your sun-java-6-plugin, but re-installing does NOT select it for re-installation ... you have to select it manually.  :)

---

### Post by Marskills on 2009-02-10
While trying to get my Terminal Server Client to switch out of Full screen mode I noticed the fix also corrected the same Firefox issue in this thread.  I first had to install compizconfig settings manager in Synaptic, then under Advanced Search select Workarounds and disable Legacy Fullscreen Support. Hope this helps.

---

### Post by wsonar on 2009-02-25
I found no matter even if I updated firefox still had problem

fixed by disabling legcy full screen support 

in compiz workarounds

firefox is all good now

---

