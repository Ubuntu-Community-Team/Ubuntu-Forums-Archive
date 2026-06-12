---
title: "Opera freezes when exit  fullscreen Youtube videos"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by beew on 2011-08-20
Go to Youtube to watch any video in any resolution, go to full screen, so far it is all good. Let it play for a bit and then exit full screen and Opera freezes even though sound is still playing in the background.  

Flash is up to date (installed with flash-aid) and Youtube works fine with FireFox. I an using Opera 11.50 in Maverick.

I am wondering if anyone has experienced the same problem and if there is a work around. Thanks.

---

### Post by scottstensland on 2011-08-20
I've had abominable experiences on ubuntu showing browser video 
however, for youtube you can opt into using html5

[http://www.youtube.com/html5](http://www.youtube.com/html5)

this has greatly reduced issues.
I'm on a fresh install on ubuntu 11.10 
without using flash aid and its STABLE at last
good luck

---

### Post by beew on 2011-08-20
It used to work and I have never experienced a problem with Firefox. HTML5 is fine but it doesn't always have the highest resolution, moreover on my machine Flash uses hardware acceleration so cpu usage is actually way lower with flash than html5.

---

### Post by beew on 2011-08-20
Ok, figured it out, installing the beta version of Flash from Adobe (using Flash-aid) solves the issue with Opera freezing but the beta version doesn't use vdpau apparently.

---

### Post by beew on 2011-08-20
P.S. It seems that this problem happens only with Youtube, tried Vimeo and maximizing/unmaximizing works fine.

---

### Post by beew on 2011-08-22
Same problem with Opera (11.50) in Natty (I started the thread because of Opera crashing in Maverick), with the stable version of flash, exiting from Youtube freezes and crashes Opera. Beta version of Flash from Adobe lap doesn't cause the freeze, but this version doesn't use VDPAU. 

I am not sure if this problem only happens when Nvidia driver is in use. Will try the stable version of flash on another install using nouveau and see what happens.

---

### Post by beew on 2011-08-22
Just checked with the Natty install with the nouveau driver, flash stable version doesn't crash Opera but there was a bit of lag going full screen to normal size windows. The experimental beta version of flash doesn't suffer any lag.

So it seems that Opera does have a bit of a problem with the latest stable version of flash on Youtube but the Nvidia driver somehow exacerbates it.

---

### Post by beew on 2011-09-20
Just updated to Opera 11.51. The problem persists, flash stable version (10.3.183.7)still crashes Opera on youtube when going from fullscreen to normal size. 

Also Opera seems to be using a lot more cpu than Firefox (without Youtube)  Wonder if others have the same problem.

I am using Ubuntu10.10 mainly but same problems exist for 11.04.

---

### Post by beew on 2011-09-20
Oh, the problem is not really solved. I have mistakenly marked the thread as solved but I can't unmark it.

---

### Post by azertyh on 2011-09-20
hello,
i haven't this issue with opera 11.51 and xubuntu 11.04.

---

### Post by Frogs Hair on 2011-09-20
I Updated to Opera 11.51 with no such problem . You could try a complete removal and installation of Opera . Remove the .hidden folders located in your home folder also . Export and save your bookmarks under Preferences > Import/Export . Opera has run like a champ for me since installing it. If that fails open a new thread so your problem gets proper attention.

---

### Post by beew on 2011-09-20
> **Frogs Hair said:**
> I Updated to Opera 11.51 with no such problem . You could try a complete removal and installation of Opera . Remove the .hidden folders located in your home folder also . Export and save your bookmarks under Preferences > Import/Export . Opera has run like a champ for me since installing it. If that fails open a new thread so your problem gets proper attention.

I have tried reinstalling Opera and the problem persists. As I said the Youtube freezing problem seems to be a combination of Opera + flash + Nvidia. Here is a basic recap: There is no problem with the beta version of flash, but vdpau doesn't work with the beta version of flash. Vdpau is enabled with the stable version of flash, but Opera freezes as a result of going from full screen back to normal screen size.

In any case the high cpu usage  have nothing to do with flash, I think I might have too many tabs opened but Opera doesn't have the feature of loading the tabs only on demand like Firefox, so cpu usage is low in FF even though I also have a lot of tabs open.

---

### Post by arneolaf on 2012-06-01
Seems like updating to Opera 12 (beta release) solved the problem in my case.

Add this to /etc/apt/sources.list or /etc/apt/sources.list.d/opera.list:
deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable non-free

This should be commented out:
# [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

---

