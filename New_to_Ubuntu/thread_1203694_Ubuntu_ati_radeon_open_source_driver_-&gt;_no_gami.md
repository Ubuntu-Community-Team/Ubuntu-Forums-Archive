---
title: "Ubuntu ati radeon open source driver -&gt; no gaming at all"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by illmatic on 2009-07-03
Hey guys,

After Upgrading to jaunty I couldn't use the closed source ati driver (or fglrx), so Ubuntu now uses the radeon driver.
Nearly everything works fine with the driver. I have no more problems with playing videos or with hybernating. But if I try to start any game it just doesnt work, or it works very slow

I got a x1900xt graphic card
I tried some hints from this guide :
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
I tried switching to XAA, but everytime I switch to XAA, I can't play any Video and I can't play any Game as well.

I was looking for any guide for setting up the driver correctly bug I could hardly find anything

Warsow for example just doesn't start and Sacred runs through wine very slow.

Greets
Illamtic

---

### Post by linuxmagick on 2009-07-03
Hmmm...

Does direct rendering show as enabled?
```
glxinfo | grep direct
```

How many frames per second are you seeing when you run glxgears?
```
glxgears
```

---

### Post by illmatic on 2009-07-04
that's the strange thing about it, direct rendering works and with glxgears i get about 4600 Frames per second.

---

### Post by linuxmagick on 2009-07-04
Here's the guide I followed to set up my ATI card in Jaunty:

```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
```

If you have desktop effects enabled, try disabling them and see if you get any better performance.

---

### Post by linuxmagick on 2009-07-04
So I decided to fire up my laptop (the only machine I have with an ATI adapter) and guess what?  I installed Warsow and tried to play and it doesn't start.  I wonder if this is just a limitation of the open source drivers?  I don't want to believe that, so I'm still researching.  If anyone has any suggestions, feel free to enlighten us.

---

### Post by SunnyRabbiera on 2009-07-04
Yeh a big complaint about the ATI open source drivers is that they are underdone compared to the closed source ones.
Maybe you should try envy to get the proprietary drivers.
Bloody ATI

---

### Post by linuxmagick on 2009-07-04
Yeah, I have to say I'm a bit disappointed then in the position AMD has put many of us in by not continuing to update the drivers for so many cards.  It's not a huge deal for me as I'm not a huge gamer and I have my desktop that has an Nvidia GTS 250 in it.  But I certainly feel the pain of those who are gamers and only have ATI cards.

---

### Post by SunnyRabbiera on 2009-07-04
Yeh I know, it feels so funny though that people say Intel is so evil by their business practices and not being that open.
But in recent years Intel has been far more open source friendly then AMD has, especially when concerning graphics drivers.
AMD has been lackluster in its linux support as of late, no wonder why Intel is kicking their @#%$%.
And even with the recent events the regressions of intel drivers intel still looks good compared to ATI.

---

### Post by illmatic on 2009-07-05
Well, the point is we got a ATI graphic accelerator, and I'm not going to buy a nvidia because they're expensive.

Now pls back 2 topic.
If I try to start warsow I get the following message: 
```
...setting fullscreen mode 4:
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  17 (XF86VidModeGetGammaRamp)
  Value in failed request:  0x27
  Serial number of failed request:  63
  Current serial number in output stream:  63
```

And Winegames like Sacred doesn't work even after reinstalling ( I just used your tutorial up there) the driver.

I know the open source driver maybe shouldn't be the fastest, but I just can't get any game working (besides tux racer or similar stuff).

And in addition I got no chance of getting the fglrx driver working because there has been no new release from ati !

I think it should be possible to play any nromal game with the open source driver.? Or can none of you play games with the open source driver?

---

### Post by ivanvajar on 2009-07-05
Guys, try new proprietary driver from ATI web site. It solved all my problems on Jaunty.

---

### Post by 3rdalbum on 2009-07-05
> **ivanvajar said:**
> Guys, try new proprietary driver from ATI web site. It solved all my problems on Jaunty.

It still doesn't support the original poster's "legacy" graphics card, which is why they are using the open-source driver.

---

### Post by ivanvajar on 2009-07-05
Then, from Recovery mode go to NETROOT and do this:

> sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg

That's as far as I can think of.

---

### Post by JillSwift on 2009-07-05
AFAIK, ATI has chosen not to support older cards with the drivers that work with the new Xorg in Jaunty.

Choices:
Go back to Intrepid.
Forgo gaming for a while, until ATI releases their drivers as open source (Don't know when, only heard the rumor.)
Get an nVidia card. :(

---

### Post by illmatic on 2009-07-05
> **ivanvajar said:**
> Then, from Recovery mode go to NETROOT and do this:



That's as far as I can think of.
That's what someone already posted. pls read what others and I wrote.

So there's no way of playing games with the open source driver?

---

### Post by ChaiTan on 2009-07-05
You'll have to wait for Gallium3D to arrive for OpenGL 2.0 and GLSL (which will improve performance).
[http://www.phoronix.com/forums/showthread.php?t=14674](http://www.phoronix.com/forums/showthread.php?t=14674)

---

### Post by oldrocker99 on 2009-07-05
I use the open source driver, and I have found that you can ramp down graphics settings in many games, turning antialiasing off, play at 800x600, etc. Consult the "settings" menu of the game you want to play, obviously. I am able to play Neverwinter Nights with everything turned off and get a barely acceptable framerate, but I can at least play my favorite game.

:guitar:

---

### Post by ssri on 2009-07-07
> **ChaiTan said:**
> You'll have to wait for Gallium3D to arrive for OpenGL 2.0 and GLSL (which will improve performance).
[http://www.phoronix.com/forums/showthread.php?t=14674](http://www.phoronix.com/forums/showthread.php?t=14674)

which will happen next summer, if lucky...

[http://www.phoronix.com/forums/showthread.php?t=17887](http://www.phoronix.com/forums/showthread.php?t=17887)

---

### Post by alphacrucis2 on 2009-07-07
> **illmatic said:**
> Hey guys,

After Upgrading to jaunty I couldn't use the closed source ati driver (or fglrx), so Ubuntu now uses the radeon driver.
Nearly everything works fine with the driver. I have no more problems with playing videos or with hybernating. But if I try to start any game it just doesnt work, or it works very slow

I got a x1900xt graphic card
I tried some hints from this guide :
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
I tried switching to XAA, but everytime I switch to XAA, I can't play any Video and I can't play any Game as well.

I was looking for any guide for setting up the driver correctly bug I could hardly find anything

Warsow for example just doesn't start and Sacred runs through wine very slow.

Greets
Illamtic

You could try the other open source driver radeonhd. I think it is in the repos. It supports some of the newer legacy cards so your card might be ok:

[http://www.radeonhd.org/ ]("http://www.radeonhd.org/")

[https://help.ubuntu.com/community/RadeonHD]("https://help.ubuntu.com/community/RadeonHD")

---

