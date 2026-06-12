---
title: "how to lower screen brightness on battery power?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-12-28
i want to set my screen brightness lower on battery power to get the best possible battery life.  but for the life of me i don't see an option to do so on power management would anyone know how to do so?

---

### Post by tom.swartz07 on 2009-12-28
> **mamamia88 said:**
> i want to set my screen brightness lower on battery power to get the best possible battery life.  but for the life of me i don't see an option to do so on power management would anyone know how to do so?

Im looking at it now and right below DISPLAY on the battery power tab it says, "Reduce backlight brightness" and "dim display when idle"

are you seeing something different?

post a screencap if you have a chance.

---

### Post by cosine352 on 2009-12-28
press Alt+F2 and paste this and hit enter or click run
> gnome-screensaver-preferences

Now go to the "power mannagment" and click on the  "On Battery Power". you should see the options there

---

### Post by mamamia88 on 2009-12-28
doesn't give an option for percentage though which i would like

---

### Post by drs305 on 2009-12-28
Do you have function button combinations on your laptop (FN and two other keys with up and down brightness symbols?  On my laptop these work in Ubuntu without me having to make any configuration changes.
(Lenovo N100)

---

### Post by mamamia88 on 2009-12-28
its a netbook and i don't see those buttons

---

### Post by hackerseraph on 2010-07-19
is there any way to adjust that percentage in gconf-editor?

---

### Post by hackerseraph on 2010-07-19
> **hackerseraph said:**
> is there any way to adjust that percentage in gconf-editor?

went looking in gconf-editor and found it. :KS

```
 
1. push alt+f2
2. type gconf-editor and open it
3. scrool to apps > gnome-power-manager > backlight
4. dim_brightness_battery -> whatever you set here is the percentage it will drop 
(ie. the higher the percentage, the greater the drop in brightness)

```

---

### Post by techunit on 2010-07-19
I use Ubuntu Tweak to change display brightness settings so they depend on the battery of the AC.. Hope this helps... There is [Video Tutorial On Ubuntu Tweak Here]("http://ubuntuvideotutorials.wordpress.com/2010/06/24/intro-to-ubuntu-tweak/")

---

### Post by hackerseraph on 2010-07-19
rofl da**it I knew i saw it in there a week or two ago. I went and looked and saw the "80" i set in gconf-manager. I feel like a tart.

---

