---
title: "X Sensors, Need Help"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by ZER01NE1NE on 2009-11-17
Hi all,

I'm trying to install X Sensors on my Ubuntu 9.10 machine, but I'm getting the typical "blank window." I've looked at forums, and I've run sensors-detect and rebooted etc. but it's still not working. Any pointers?

~ Kyle

---

### Post by RedSingularity on 2009-11-19
Your not the only one.  I never could get that working.  I had to use screenlets sensors to view hardware information.

---

### Post by Zoot7 on 2009-11-19
TBH Xsensors hasn't worked for me since Hardy (8.04).

The sensors applet is what I use:
```
sudo apt-get install sensors-applet
```

You can just right click and add it the panel.

---

### Post by ZER01NE1NE on 2009-11-20
OK thanks, but what's the command for it? Is it just sensors?

---

### Post by doas777 on 2009-11-20
the command installs sensors-applet which is a gnome panel applet that displays the output of libs like lm-sensors. usually I use it to monitor my cpu/gpu temps. on some boxes, where the apic correctly exposes the fan speed and voltage sensors, it can display them too.

to install with lm-sensors, just do this:
```
sudo apt-get install lm-sensors sensors-applet
sudo sensors-detect  (answer yes to every question. there is one that defaults to "no" so be careful)
sudo reboot

```

if you want cli output from lm-sensors the command is, as you say, 'sensors'

---

### Post by ZER01NE1NE on 2009-11-21
OK, thanks, I found something to add to the bottom bar that says "Hardware Sensors Monitor," is that it?

---

### Post by doas777 on 2009-11-21
> **ZER01NE1NE said:**
> OK, thanks, I found something to add to the bottom bar that says "Hardware Sensors Monitor," is that it?
bingo

---

