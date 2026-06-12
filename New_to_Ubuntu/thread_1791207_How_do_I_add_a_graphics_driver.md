---
title: "How do I add a graphics driver?"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by bluetortilla on 2011-06-26
I have a laptop with an external monitor. I've had no success in getting the laptop monitor to toggle off during sessions. I found out I have an Intel Pentium M CPU (1.2 GHz) and an Intel GM 828521 Graphic Controller (chip not card?). I did not know that info before.

How do I manually add the driver so I can work the monitors  (Ubuntu 11.04)?

Thanks!

---

### Post by wolfen69 on 2011-06-26
The intel drivers are already installed. Ubuntu comes with them. Have you checked display settings?

---

### Post by bluetortilla on 2011-06-27
> **wolfen69 said:**
> The intel drivers are already installed. Ubuntu comes with them. Have you checked display settings?

Yes. Same as before: Unknown.

Ran Additional Drivers. Nothing. The laptop is fairly old (Panasonic Let's Note/Toughbook series).

---

### Post by mastablasta on 2011-06-27
toggle off? you mean suspsed? that has to do with motherboard i believe. and power management.

---

### Post by bluetortilla on 2011-06-28
> **mastablasta said:**
> toggle off? you mean suspsed? that has to do with motherboard i believe. and power management.

No. Just turn off the laptop monitor. That's all I want to do. Everything else is fine.

---

### Post by Mark Phelps on 2011-06-28
> **bluetortilla said:**
> No. Just turn off the laptop monitor. That's all I want to do. Everything else is fine.

You typically do that by pressing a function key on the laptop.  On mine, it is F10 -- it has a screen symbol on it.

---

### Post by bluetortilla on 2011-06-28
> **Mark Phelps said:**
> You typically do that by pressing a function key on the laptop.  On mine, it is F10 -- it has a screen symbol on it.

Yes, that does not work.It's F3 on mine, but I tried them all anyway!

I think I need to configure the driver manually, but I have no idea how.

---

### Post by idoitprone on 2011-06-28
i only know commandline
turn off
```
xrandr --output LVDS1 --off

```

turn it back on
```
xrandr --output LVDS1 --auto
```

```
xrandr -q
```

replace the LVDS to the one shown in xrandr -q

---

