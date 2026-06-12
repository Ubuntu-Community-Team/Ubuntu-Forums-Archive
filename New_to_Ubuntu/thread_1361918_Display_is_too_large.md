---
title: "Display is too large"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by milesorvana on 2009-12-22
Ok, i just returned from a friend's house with my computer because my sound wasn't working. Luckily we found out that i was booting to an older kernal and that was the problem but for some reason now my display seems to be twice as large. My monitor is an**[SIZE=1] eMachines® E17T4W 17" Widescreen LCD Monitor. [/SIZE]**[SIZE=1]However, under the display settings it says it can not detect my monitor and i can't choose a higher resolution. The Highest i can pick is 800 x 600 (4:3) and the refresh rate is locked at 60 Hz (can't pick anything else). Here is the technical info about the monitor:

[/SIZE]> Viewable Area: 17" viewable (diagonal)Widescreen 16:9 Aspect Ratio Panel Type: LCD active matrix TFT WXGA Resolution: 1280 × 720 (native and maximum) Dot Pitch: 0.291mm Brightness: 250 cd/m² Contrast Ratio: 500:1 Response Time: 8ms Screen Treatment: Antiglare Colors: 16.2 million User Controls: Power on/off button, on screen display menu control buttons Viewing Angles: 140° left/right, 130° up/down Signal Inputs: Analog (VGA) Ports: AC power input, Kensington security lock slot Agency Certifications: Energy Star® , UL, cUL, FCC Class B, NOM, CE, VCCI, CB, RoHS Display Stand: Included (adjustable tilt) Mount: Compatible with VESA (4 × 100mm) compliant mounting solutions Electrical Requirements: 20 watts (normal operation)/1 watt (power-save)100-240 VAC, 50/60Hz

---

### Post by Don Gatto on 2009-12-23
Hi,

You might try
```
xrandr --output VGA --mode 1280x720 --rate 60
```
in the Terminal. I'm not sure if this is a permanent fix or it will vanish with the next reboot.
You shouldn't worry about the 60 Hz refresh rate though, it's the native and perfect value for the LCD/TFT monitors.

---

### Post by milesorvana on 2010-01-23
I am not sure if anyone else has looked at this for me, but i still am suffering from the problem.

---

### Post by halitech on 2010-01-23
what video card do you have?

---

### Post by milesorvana on 2010-02-03
I have no idea what video card i have. It is just the video card that comes in the T3522 desktop.

---

### Post by Don Gatto on 2010-02-04
According to the official [site]("http://emachines.com/support/product_support.html?cat=Desktops&subcat=T%20Series&model=T3522"), it has an integrated Intel® Graphics Media Accelerator 900.

---

### Post by nhasian on 2010-02-04
> **milesorvana said:**
> I have no idea what video card i have. It is just the video card that comes in the T3522 desktop.

please open a terminal from Applications->Accessories->terminal and give us the output of the following commands:

```
lsb_release -a
```
```
lshw -C display
```

---

### Post by superprash2003 on 2010-02-04
have you looked under system->admin->hardware ?

---

