---
title: "Splash Image Issues"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by shoaibi on 2009-12-11
I am running Karmic Koala, fully upgraded. I have install startupmanager to change the usplash but no matter which usplash i see a strange splash image with circles, color meter, rectangles, just like when you are playing with a monitor's settings...

right now i tried [http://www.ubuntu-art.org/content/show.php/Dell+Usplash?content=92805](http://www.ubuntu-art.org/content/show.php/Dell+Usplash?content=92805) with startupmanager run from commandline to checkout any errors/warnings but everything went fine and i still get that weird usplash from 80s.

---

### Post by bodhi.zazen on 2009-12-11
9.10 now uses xsplash so I am not sure how far you are going to get with usplash.

---

### Post by shoaibi on 2009-12-11
hmmmm, and any resource to get xsplash images? or to convert usplash to xsplash?

---

### Post by shoaibi on 2009-12-11
and btw xsplash is for gdm theming, right?
I want to change the bootup screen, then one that shows white ubuntu logo.... the one before loading gdm...

---

### Post by bodhi.zazen on 2009-12-11
This thread may help you : [http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683)

I can not tell if you are wanting to change your grub splash, xsplash, or GDM theme ;)

---

### Post by ranch hand on 2009-12-11
I would suggest reading the link in my sig so thatt you have a better idea of what grub2 is all about.

I think this is the best in depth link on grub2;

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I also would encourage you to remove SUM.  It is not going to be very helpful yet and may well stop you from doing some things.  Give the guy a chance to get it updated to function right with grub2.

---

### Post by adaucourt on 2009-12-11
> **shoaibi said:**
> I am running Karmic Koala, fully upgraded. I have install startupmanager to change the usplash but no matter which usplash i see a strange splash image with circles, color meter, rectangles, just like when you are playing with a monitor's settings...

right now i tried [http://www.ubuntu-art.org/content/show.php/Dell+Usplash?content=92805](http://www.ubuntu-art.org/content/show.php/Dell+Usplash?content=92805) with startupmanager run from commandline to checkout any errors/warnings but everything went fine and i still get that weird usplash from 80s.

i think this is what your are going for?
[https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming)

```
sudo apt-get install grub2-splashimages
```

---

### Post by shoaibi on 2009-12-11
> **bodhi.zazen said:**
> This thread may help you : [http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683)

I can not tell if you are wanting to change your grub splash, xsplash, or GDM theme ;)

Lets have a walk through:
(In General):
BIOS Screen -> Grub -> Boot Screen with white ubuntu logo in the mid of screen-> GDM starts with the brown background, ubuntu logo and progress bar -> shows login

I wanna change the screen that appears "after" grub, the one with the white ubuntu logo in the mid of the screen.

Xsplash as far as i can understand deals with gdm, as i "have" changed it and thus my login windows have show great improvements, but i am interested the in the screen before even GDM starts.

---

### Post by QIII on 2009-12-11
It seems that the most recent grub2-splashimages installs a slightly different etc/grub.d/05_debian_theme, so those instructions may be a little dated.

I installed it on my Lucid machine -- after saving my original /05_debian_theme -- and have been looking through it to make sure that I get the new one right.

---

### Post by joes7 on 2009-12-11
re-install grub from the live cd

---

### Post by joes7 on 2009-12-11
you can always upgrade by writing the following line on a terminal
```

upgrade-grub

```

---

