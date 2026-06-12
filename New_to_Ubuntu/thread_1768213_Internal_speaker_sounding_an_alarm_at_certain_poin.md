---
title: "Internal speaker sounding an alarm at certain points"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by GODDAMN FOOL on 2011-05-26
My internal speaker starts sounding an alarm at certain points and I'm not sure what is exactly causing it.  I've been able to reproduce it in three instances: 
a) playing a Java game on my browser (e.g. Runescape, Minecraft) - the alarm will cease when I pull up a menu in Minecraft or switch to a new tab in the browser
b) watching a video in my browser (has only happened to the videos on [www.chipandironicus.com]("http://www.chipandironicus.com"), but not youtube)
c) when running Steam through Wine

I don't think it's an overheat alarm as I don't believe it'd be so easy to make stop by opening a menu or switching tabs.  Also, the temperature gauge on my case isn't showing any sign of high temps.  I receive no performance hit, either, so I'm ruling out overheating.

First of all, is there a way to perhaps check to see for what reason the alarm is sounding?  This is a rather old computer, but for what I'm using it for it's still pretty powerful
(I'm not even sure where to find the device listing since everything's been so shuffled around since the last update)

Geforce 6800GT
Audigy 2
1GB RAM
I don't even remember what the processor is, but it's sufficient

---

### Post by Dondermans on 2011-05-26
> **GODDAMN FOOL said:**
> My internal speaker starts sounding an alarm at certain points and I'm not sure what is exactly causing it.  I've been able to reproduce it in three instances: 
a) playing a Java game on my browser (e.g. Runescape, Minecraft) - the alarm will cease when I pull up a menu in Minecraft or switch to a new tab in the browser
b) watching a video in my browser (has only happened to the videos on [www.chipandironicus.com]("http://www.chipandironicus.com"), but not youtube)
c) when running Steam through Wine

I don't think it's an overheat alarm as I don't believe it'd be so easy to make stop by opening a menu or switching tabs.  Also, the temperature gauge on my case isn't showing any sign of high temps.  I receive no performance hit, either, so I'm ruling out overheating.

First of all, is there a way to perhaps check to see for what reason the alarm is sounding?  This is a rather old computer, but for what I'm using it for it's still pretty powerful
(I'm not even sure where to find the device listing since everything's been so shuffled around since the last update)

Geforce 6800GT
Audigy 2
1GB RAM
I don't even remember what the processor is, but it's sufficient

Which Ubuntu version are you using?

Open a terminal and enter ```
sudo lshw -html > configuration.html
```That will save configuration.html in your home folder.

---

### Post by GODDAMN FOOL on 2011-05-26
I'm using 11.04, however this happened with 10.10, too

A little more of the hardware listing: 

AMD Athlon(tm) 64 Processor 3400+
SB Audigy (not an Audigy2 like previously mentioned)

---

### Post by GODDAMN FOOL on 2011-05-27
I cleaned out the fans and heatsink and my CPU is running a bit cooler now, but I still don't think that had any bearing on the alarm considering it seemed to run in context with the menus of the games.  I'm still looking for any second opinions on what anyone might think it is?  Perhaps a Java problem?

---

### Post by Prince Valiant on 2011-05-27
Have you tried poking around in the BIOS settings to see if there are setting there which control the alarm?

-Val

---

