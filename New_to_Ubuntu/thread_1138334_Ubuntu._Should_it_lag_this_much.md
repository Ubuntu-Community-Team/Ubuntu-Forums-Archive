---
title: "Ubuntu. Should it lag this much?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Pas_sa on 2009-04-26
Hi folks. Got some issues with Ubuntu on my laptop. I've had it on in the past (had to remove it due to HDD size constraints), plunked it back on after getting a larger HDD, but I'm having issues with it.

Running an updated version of 9.04, it just lags. Menus at the top of the screen take 2-3 seconds to fully render, switching tabs in Firefox is labouriously slow (it is also slow in Epiphany), switching between open apps is slow.. I daresay it reaches unusable levels. I run XP on the machine as well and it is far more responsive and zippy.

Specs are:
Pentium M 1.4GHz, 1.5GB RAM, 32MB Radeon 7500.

My first thought was to disable visual effects.. which I did.. but performance hasn't improved noticably. Is there something I'm missing here? Is Gnome seriously too much for my machine?

---

### Post by Vunutus on 2009-04-26
I haven't upgraded yet, personally, but I hear lots of people are having lag issues like that in Jaunty. Perhaps open up the system monitor and see what your CPU/memory load is like?

---

### Post by Pas_sa on 2009-04-26
Well, I upgraded from 8.10 and that was also fairly laggy. I tried to dismiss it as me just being picky but it became pretty bleedingly obvious when I was using my desktop alongside the laptop. Desktop is MUCH more responsive in Ubuntu than XP.

Say I have a foreground window on my browser and I minimise it.. I'll see the window underneath take 2-3 seconds to 'redraw' before I can grab focus of it and use it. Hence I'm concerned it might be a video problem..

---

### Post by philinux on 2009-04-26
Could be vid driver related.

---

### Post by Pas_sa on 2009-04-26
Says I have direct rendering enabled. Even things like changing the wallpaper.. it tries to fade between them but instead the whole system locks up and the laptop slowly fades between them.

Something *ain't right*.

---

### Post by ugriffin on 2009-04-26
That happened with some Intel chipsets on the jump to Jaunty, but I've never heard of this in an ATI card.


Solution 1) Get an nvidia :P

Could you give me the exact specs of your video card, please?

---

### Post by Pas_sa on 2009-04-26
Uhh.. it's a Mobility Radeon 7500.. has 32MB VRAM.. interfaces with AGP.. R100 based (hence isn't supported by even fglrx, but whatever it uses by default provides direct rendering).

Video playback of Xvid and DivX files is fine. Though in 8.10, VLC never split into an 'XVideo' window and a playback controls window.. *sigh*

Oh and just for the sake of it..
```
andrew@andrewlaptop:~$ glxgears
3121 frames in 5.0 seconds = 623.858 FPS
3186 frames in 5.0 seconds = 636.952 FPS
3197 frames in 5.0 seconds = 639.353 FPS
3194 frames in 5.0 seconds = 638.678 FPS
3172 frames in 5.0 seconds = 634.334 FPS
```

And yeah, believe me, if this wasn't a laptop (or if I'd chosen the laptop myself ;)), it'd be running an Nvidia card. Like my desktop is. Not a fan of ATI's stuff under Linux or Windows.

---

### Post by eilios on 2009-04-26
> **Pas_sa said:**
> Uhh.. it's a Mobility Radeon 7500.. has 32MB VRAM.. interfaces with AGP.. R100 based (hence isn't supported by even fglrx, but whatever it uses by default provides direct rendering).

Video playback of Xvid and DivX files is fine. Though in 8.10, VLC never split into an 'XVideo' window and a playback controls window.. *sigh*

Oh and just for the sake of it..
```
andrew@andrewlaptop:~$ glxgears
3121 frames in 5.0 seconds = 623.858 FPS
3186 frames in 5.0 seconds = 636.952 FPS
3197 frames in 5.0 seconds = 639.353 FPS
3194 frames in 5.0 seconds = 638.678 FPS
3172 frames in 5.0 seconds = 634.334 FPS
```And yeah, believe me, if this wasn't a laptop (or if I'd chosen the laptop myself ;)), it'd be running an Nvidia card. Like my desktop is. Not a fan of ATI's stuff under Linux or Windows.
If you want a good laptop, check out system76. My friend got a laptop from there and he loves it. Anyways, back on topic. To absolutely slay lag, get Dillo. It will get rid of all lag issues imaginable(I ran it on a VM with 128 mb of ram and it ran like a dream, only like 32 mb of vram too). Xubuntu should also signifigantly reduce lag. If you get those two, you should have smooth sailing.

---

### Post by Pas_sa on 2009-04-26
I don't really think it's a browser thing since the OS is sluggish without Firefox being open (and surely Epiphany isn't heavy on resources since that lags as well). System monitor reports I'm only using a fraction of my 1.5GB of RAM and none of my swap, and CPU usage is pretty low. This is bizarre.

I'm quite used to Gnome and would like to avoid having to switch to Xubuntu at all costs.. any other ideas? (especially if we run with this 'its the video card' idea)

---

### Post by Pas_sa on 2009-04-27
*sigh*

I checked my CPU speed with 'cat /proc/cpuinfo'

Says I'm running at 600mhz despite my CPU being 1.4GHz. I'm going to go out on a limb and guess that's why Ubuntu is as laggy as hell.

Seems it's going nuts with power management. Can't find any options on how to fix that. How can I alter how it changes my clock speed? In my IBM BIOS, I've set it to run flat out when on AC, but this obviously isn't the case.

---

### Post by alphacrucis2 on 2009-04-27
> **Pas_sa said:**
> 
Video playback of Xvid and DivX files is fine. Though in 8.10, VLC never split into an 'XVideo' window and a playback controls window.. *sigh*



The VLC devs did that on purpose, as there was a bug that caused problems playing vids in the main VLC window on Linux. The issue is completely resolved in VLC version 1 which is still prerelease but can be installed from Kow's PPA:

> [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

---

### Post by satandole666 on 2009-04-27
I'm having significant trouble using 9.04 with 512mb ram, a P4 1.6ghz, and a ATI Mobility 7500 16mb card as well.

I've been experimenting with all of the various Mobility 7500 tweaks (there are a ton of posts about it when searched) and I haven't found anything to improve my 2D performance.  The scrolling in webpages is horribad.  The same goes with a 2D browser game I play along with any video/streaming video playback.

Wish I could be more help, but this was the starting point for me:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

So far it has been a trade-off.  I can get better 2D performance somewhat (using some of the tweaks at the bottom of the page) but it comes at the cost of 3D performance.  I'll post anything if I can get major results.

---

### Post by cracksquirrel on 2009-04-27
I am also experiencing major lag on the UI after upgrading to 9.04 from 8.10. 

Sony Vaio
Intel Centrino Duo 2.0 
2 gigs ram
Intel 945 video

lags on everything that requires rendering basically.. :)

---

### Post by crabclaw on 2009-04-29
Also experiencing lag. Never experienced this much lag with any other Ubuntu release. Everything apart from that is pitch-perfect. When it works it's snappy as hell. Then everything will just fall apart for a couple of hours. Have checked system monitor and nothing particularly out of the ordinary. RAM being used out of a possible 1.5GB never tops 20%! Is there some way of forcing ubuntu to use all the RAM?

edit:
Just found this on an external site, does anyone know if this'll make much of a difference?

sudo aptitude purge xserver-xorg-video-i740

---

### Post by Mortus Pryde on 2009-04-29
I think Jaunty has a few bugs regarding Intel and ATI video systems. Jaunty should have EXA rendering enabled by default in Mesa the open source 3D driver used in Jaunty, you can try changing this to XAA in the xorg.conf file? and see if that helps, sorry still a novice so I don't have the exact line commited to memory, but I am sure those more experianced will and can help you with how to do so.

I am currently still running Intrepid on my IBM with a 9600, but I am using the proprietory driver as my graphics system is not fully supported under open sourse drivers and I require that a few applications.

---

### Post by Fayte2071 on 2009-04-29
> **ugriffin said:**
> That happened with some Intel chipsets on the jump to Jaunty, but I've never heard of this in an ATI card.


Solution 1) Get an nvidia :P

Could you give me the exact specs of your video card, please?

Well, I just installed 9.04 actually on my laptop and I have the same problem and it's quite irritating. I actually have an Intel chipset, is there a fix for it?

---

### Post by Fayte2071 on 2009-04-29
.

---

### Post by crabclaw on 2009-04-29
I don't know if this'll be of any use to you but my computer was lagging a good deal. i switched off advanced desktop settings and it all stopped. Now personally I'm not a great ubuntu know-how person but I've tweaked a ton of things to exactly the way I like them and the advanced settings were never really a part of that. Turning visual effects settings to normal has given me a really incredibly speedy and pleasant OS. 

I realise this isn't exactly 'advice' as such but I reckon the graphics cards get put under alot of strain in ubuntu since we expect so much from 'em to put other OS' in the shade. Slowing down the load makes an incredible difference.

---

