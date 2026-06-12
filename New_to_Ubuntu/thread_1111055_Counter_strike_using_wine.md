---
title: "Counter strike using wine ??"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by kshtjsnghl on 2009-03-30
Hi 
I installed counter strike 1.6 using wine. But as soon as i started playing on any map in around about 1-2 minutes graphics fail. All the players appear to be black ( no difference between terrorists and counter terrorists :( ). Moreover after some 15 mins, even the game's sound goes off. Restarting helps but again it comes to the same stage.

 I tried to change the options given in the video option - Open GL, Software and D3D but nothing helps. In spftware mode, i can distinguish between the players but the maps graphics are too low.

Anyone who has faced the same problem or knows how to tackle it please reply.

PS : The system configuration is good enough to support counterstrike coz i have played it on windows with 1 GB lesser.

---

### Post by northern lights on 2009-03-30
Most likely this bug is specific to your hardware setup.

CS under Linux appears to run a lot smoother on machines with nvidia graphics chipsets rather than on those with ATI devices.

You can check for a solution at [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507"). Probably you best bet in finding someone with the same problem.

Posting specs is always a good idea also.

---

### Post by kshtjsnghl on 2009-03-30
my hardware includes - 

intel media accelerator 128 mb
945gm chipset
1.5 gb ram
duo core processor 1.6Ghz

---

### Post by LowSky on 2009-03-30
intel integrated chips have never been know to play any videogames very well.

---

### Post by necronwarrior on 2009-03-30
I am having a problem running CS on ubuntu too...................
everything works fine with the graphics but the the only problem is that there is no sound!!!!!!
in fact there is no sound in any applications run in wine.
I have a core 2 duo with 2 gb of ram.

---

### Post by aktiwers on 2009-03-30
Have you tried [Wine-doors]("http://wddb.wine-doors.org/downloads")?

Else try go into:
```
winecfg
```And change your audio-settings

---

### Post by kshtjsnghl on 2009-03-30
Sound settings are fine i just checked them.
Anyways sound goes mute after some time.

> intel integrated chips have never been know to play any videogames very well.

but i have played the same version on windows using 512 ram.

> Have you tried Wine-doors?

What is it? How will it help.

---

### Post by aktiwers on 2009-03-30
Wine-doors automatically installs windows apps and games and configures wine to work with them.

Try it out, if I remember correct, it creates a new instance of Wine for each app you install or a new config file so that your apps runs like they are rated to do in the wineappdb, 
without you having to configure it manually. Steam works great here this way.

---

### Post by necronwarrior on 2009-03-31
> **aktiwers said:**
> Have you tried [Wine-doors]("http://wddb.wine-doors.org/downloads")?

Else try go into:
```
winecfg
```And change your audio-settings
Yes i have tried changing to the different sound drivers but still no avail....
I will try out wine doors and let you know if that works out..

---

### Post by tarps87 on 2009-03-31
> **necronwarrior said:**
> I am having a problem running CS on ubuntu too...................
everything works fine with the graphics but the the only problem is that there is no sound!!!!!!
in fact there is no sound in any applications run in wine.
I have a core 2 duo with 2 gb of ram.

Try opening wine config under the applications menu (or run winecfg), select the audio tab and the set the sound device to alsa.

> **kshtjsnghl said:**
> but i have played the same version on windows using 512 ram.


WINE is not windows, you are trying to run it on a translation layer so I is likely to effect game play.
Also the graphics will be controlled by the graphics car not the amount off ram.
I would suggest trying a different graphics card or running it on the os it was compiled for.

---

### Post by necronwarrior on 2009-04-03
> **tarps87 said:**
> Try opening wine config under the applications menu (or run winecfg), select the audio tab and the set the sound device to alsa.
WINE is not windows, you are trying to run it on a translation layer so I is likely to effect game play.
Also the graphics will be controlled by the graphics car not the amount off ram.
I would suggest trying a different graphics card or running it on the os it was compiled for.
I have tried to set the audio device to ALSA but still the sound wont work.I have tried to play Counter strike on ubuntu 8.04 and 8.10 on my friends laptop(he has the exact same configuration as mine)and it has worked perfectly.
I have installed wine doors.now doI have to install C.S again or would the executable work???

---

### Post by AnojiRox on 2012-02-14
If your computer is quite fast, I suggest downloading a vm center (like oracle's virtualbox) and Installing some version of windows on. works fine for me :tongue:

---

### Post by sffvba[e0rt on 2012-02-14
Back to sleep old thread...


404

---

