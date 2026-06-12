---
title: "OpenGL fullscreen cut-off issue"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by El Lance-O on 2010-08-13
I have been having this issue for about 2 years now, and I still have not been able to find an answer. I hope someone will help me this time around.

The issue is that in GFCEU (nintendo emulator) and OpenMSX (MSX emulator) amongst other games (Diablo 1 under wine) whenever I start a game in fullscreen, it stretches the image past the bottom of my screen.

It's not a matter of it being positioned wrong, but rather it thinks my screen is lower than it really is.

There is only one other thread that is exactly what I am experiencing:
[http://ubuntuforums.org/showthread.php?t=791527](http://ubuntuforums.org/showthread.php?t=791527)

I have tried taking screenshots, screencap videos, etc of this issue, but nothing will capture what is going wrong.

Can anyone tell me how to correct this OpenGL bug, or direct me to a bugreport?  This is 2 years overdue, and REALLY irritating me.

I am running on an nVidia 7300go (crap I know), on an Inspiron 1505n Dellbuntu. Please please please someone help! :(

---

### Post by Vaphell on 2010-08-14
i assume you got widescreen monitor. Try setting nvidia driver to use hardware scaling with fixed aspect ratio. This should display 640x480/800x600 in pillar mode where 4:3 is forced to stay within monitor height and you get distortion free picture in original 4:3 aspect ratio with black bars on sides.
I had similar problem when i tried to play d2 - because of your post i decided to test how thing look now. I get perfectly positioned picture (with bars) but my ati decided to overlay desktop panels on top and i can't click a thing (it's usable with compiz disabled). It may work better with your nvidia though, as their drivers are of higher quality.

edit: it appears you can make things better when compiz is enabled
Compiz config panel - general options - checkbox 'unredirect fullscreen windows'

---

### Post by El Lance-O on 2010-08-14
I've tried every combination of those settings in 'nvidia-settings' with no luck.

I need Compiz to be disabled as it causes my USB speakers to start crackling for some reason whenever it is enabled.

---

### Post by Vaphell on 2010-08-14
well, i checked out diablo 1 - it's crap >_<  i got oddball scaling and other issues with rendering (no fire, pentagrams don't refresh so there were 4 of them at any time)

---

### Post by El Lance-O on 2010-08-14
I was aware of Diablo 1 graphical issues, but once you get in the game it runs just fine, but still with scaling issues.

But this isn't JUST Diablo, but several other OpenGL applications as well, which raises my concern.

---

### Post by Vaphell on 2010-08-14
you are right, gameplay part works - and it fits inside the boundaries of my screen. Does d1 really have to run in  opengl mode?
out of curiosity i installed gfceu and gave 1 downloaded rom a ride. In fact it was fugly in opengl mode (artifacts). In all honesty i'd prefer to play without acceleration, it was ok without it. Hardware scaling in gfx card properties didn't work at all when i tried to go fullscreen, picture size was indentical in window and fullscreen mode. I got fullscreen only after i switched gfx scaling off. Yes, it's a mess :)

do non-opengl apps run ok?

---

### Post by El Lance-O on 2010-08-16
Yes, everything else that runs fullscreen is fine. But anything with OpenGL it seems, cuts off the lower 1/5 of the screen.

---

### Post by freeware.preacher on 2010-08-19
I have the same problem with ColdWar (and any other full screen game). I've fiddled with my Nvidia and Compiz settings with no luck! Any ideas?

---

