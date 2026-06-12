---
title: "Desktop effects"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by itsvan on 2009-02-01
HI,i just reinstalled a fresh copy of Ubuntu Hardy, and i was wondering what to install to be able to do all the Cool Ubuntu effects, like the 3d windows and what not,any ideas??

---

### Post by Crafty Kisses on 2009-02-01
First thing is you have to make sure you have your graphics card drivers installed, then you can install this package:
```
sudo apt-get install compizconfig-settings-manager
```
Then from there you can select what effects and stuff you want.

---

### Post by &#32 Greg on 2009-02-01
Also 

sudo apt-get install fusion-icon

for added usability.

---

### Post by Nightstrike2009 on 2009-02-01
My how-to for (Ubuntu 8.10) thread is here:[http://ubuntuforums.org/showthread.php?t=1035634]("http://ubuntuforums.org/showthread.php?t=1035634")
I am new too this covers everything you need for NVidia Drivers (use 177) Compiz set-up and basic 3D cube & relection settings. *No commandlines or xorg setup required, simple and easy* Hope it helps you ;-)

**UPDATE:** Whoops sorry your Ubuntu is 8.04LTS isn't it? This won't work on that version tried it before, sorry my mistake :-(

---

### Post by itsvan on 2009-02-01
I had another question,,for some reason my video card is detected but the resolution doesnt go past a certain number,,"1024X769" what can i do to fix ths?

---

### Post by stchman on 2009-02-01
> **itsvan said:**
> HI,i just reinstalled a fresh copy of Ubuntu Hardy, and i was wondering what to install to be able to do all the Cool Ubuntu effects, like the 3d windows and what not,any ideas??

What kind fo video card do you have?  Compiz is enabled by default on Hardy and later.

---

### Post by Nightstrike2009 on 2009-02-01
If you also downloaded NVidia settings have you tried that, that may let you change it to a different resolution?

---

### Post by itsvan on 2009-02-01
I have an Nvidia Geforce series 7800..im really new at this,,so i dont know what drivere to get or what,,the resolution was fine until i installed compiz

---

### Post by Nightstrike2009 on 2009-02-01
I would get my drivers from [http://packages.ubuntu.com/hardy/misc/]("http://packages.ubuntu.com/hardy/misc/") (You can download dependacies here to) but you would have to find out which drivers to use from one of the others as i don't use the same version (it will start with "nvidia-" from the list)

---

### Post by stchman on 2009-02-01
> **itsvan said:**
> I have an Nvidia Geforce series 7800..im really new at this,,so i dont know what drivere to get or what,,the resolution was fine until i installed compiz

Enable the Nvidia driver in:

System--->Administration--->Hardware Drivers

Compiz will work as soon as you reboot.

---

### Post by itsvan on 2009-02-02
its weird because i deactivated my Nvida harware and the resolution works perfectly,,it gives me way more options,,but now i cant use the desktop effects! waht can i do?

---

### Post by stokedfish on 2009-02-02
Just install KDE 4.2 and use KWin!    ;)

Compiz sucks. It's a mess...

---

### Post by itsvan on 2009-02-02
how do i install all of that? sorry im new to this and dont want to mess it up

---

### Post by SunnyRabbiera on 2009-02-02
> **stokedfish said:**
> Just install KDE 4.2 and use KWin!    ;)

Compiz sucks. It's a mess...

Me I never had any real issus with compiz.

---

### Post by Crafty Kisses on 2009-02-02
> **stokedfish said:**
> Just install KDE 4.2 and use KWin!    ;)

Compiz sucks. It's a mess...

I think Compiz is really good! I've never had any problems at all.

---

### Post by itsvan on 2009-02-02
what should i do then? im rather confused

---

