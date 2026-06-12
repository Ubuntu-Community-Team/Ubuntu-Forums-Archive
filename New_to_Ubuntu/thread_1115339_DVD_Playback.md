---
title: "DVD Playback"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by funkdified on 2009-04-03
I followed this guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Prior to following that guide I followed the guide at medibuntu.

I Live in NZ and have changed my DVD region code to 4 (NZ)

I continue having the exact problem I had before doing any of this.. 

When I open a DVD in VLC or movieplayer the window opens as if the dvd is about to start playing.. then the app closes all together in an instant.. 

I have tried EVERYTHING.. and somehow in XP all I do is pop the DVD in and away I go.

Please HELP.. I really want to be rid of XP forever, but until I get these basic functions working, I am still relying on the other boot =(

---

### Post by SunnyRabbiera on 2009-04-03
even after installing libdvdcss?
Very odd, maybe trying another player might work, for me I ditched the default player for DVD's and use xine for my DVD needs.
Xine is a good app for playing DVD's
Smplayer might also be something good to try as well.

---

### Post by funkdified on 2009-04-03
odd indeed.. i have tried VLC and gxine... as well as totem.. all the same issue.

---

### Post by SunnyRabbiera on 2009-04-03
Well try smplayer next, its possible something is missing here though.
Usually installing libdvdcss works for most DVD's though.
Are these home made DVD's?

---

### Post by sneeks on 2009-04-03
very odd,i was gonna read the link you had,but it was all......too much.
have you installed all the g streamer codecs,good,bad and ugly,etc.
i know normally doing the libs should do it but give it a try.
i have cousin in nz and it worked for him.

---

### Post by stchman on 2009-04-03
> **funkdified said:**
> I followed this guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Prior to following that guide I followed the guide at medibuntu.

I Live in NZ and have changed my DVD region code to 4 (NZ)

I continue having the exact problem I had before doing any of this.. 

When I open a DVD in VLC or movieplayer the window opens as if the dvd is about to start playing.. then the app closes all together in an instant.. 

I have tried EVERYTHING.. and somehow in XP all I do is pop the DVD in and away I go.

Please HELP.. I really want to be rid of XP forever, but until I get these basic functions working, I am still relying on the other boot =(

The DVD CSS algorithm is copyrighted so Ubuntu cannot include it in a default install.  Windows XP it is not included in default install unless OEM installed it for you.

This works:

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by funkdified on 2009-04-03
well smplayer gets further than the others and plays the music from the DVD MENU and the app doesnt die.  Still no video though. Yes, I have installed all of the codecs and everything from medibuntu/the other link I put above.

---

### Post by funkdified on 2009-04-03
> **stchman said:**
> The DVD CSS algorithm is copyrighted so Ubuntu cannot include it in a default install.  Windows XP it is not included in default install unless OEM installed it for you.

This works:

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

I did this already with the medibuntu guide.. but I did it once more for good measure.. Still no luck.

---

### Post by philinux on 2009-04-03
Have you tried...

1. turning compiz off. system>prefs>appearance>visual effects>none.

2. system>admin>hardware drivers. Check for any offered to be installed/activated.

---

### Post by stchman on 2009-04-03
> **funkdified said:**
> I did this already with the medibuntu guide.. but I did it once more for good measure.. Still no luck.

Works for me on all my PCs with DVD drives.

---

### Post by funkdified on 2009-04-03
> **philinux said:**
> Have you tried...

1. turning compiz off. system>prefs>appearance>visual effects>none.

2. system>admin>hardware drivers. Check for any offered to be installed/activated.

i read somewhere that there was no need to use restricted drivers for ATI video cards.. but this is not true.. i can now have visual effects turned on and watch the dvd from any program without problem.. interestingly turning off the visual effects enabled DVD playback without the restricted driver.. but with it i can have both.. thanks phil!

UPDATE: DVD playback using my new gfx card driver was poor with the visual effects on, with them off it looks very smooth.. good to know

---

### Post by philinux on 2009-04-03
> **funkdified said:**
> i read somewhere that there was no need to use restricted drivers for ATI video cards.. but this is not true.. i can now have visual effects turned on and watch the dvd from any program without problem.. interestingly turning off the visual effects enabled DVD playback without the restricted driver.. but with it i can have both.. thanks phil!

Marvelous, thought it might be that.

---

### Post by richg on 2009-04-03
I could not view DVDs using 8.04 or 8.10. My workaround was to replace Ubuntu with Mint 6 which is based on Ubuntu 8.10. Plays DVDs right out of the box with no work under the hood.
Ubuntu does have better forum support though.

Rich

---

### Post by SunnyRabbiera on 2009-04-03
> **richg said:**
> I could not view DVDs using 8.04 or 8.10. My workaround was to replace Ubuntu with Mint 6 which is based on Ubuntu 8.10. Plays DVDs right out of the box with no work under the hood.
Ubuntu does have better forum support though.

Rich

Yes though any issue Mint has can be solved by most of the solutions you see here.

---

### Post by Garrovick on 2009-04-03
I used this page.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Works on my machine.

---

