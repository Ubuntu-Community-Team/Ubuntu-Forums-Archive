---
title: "nvidia names for monitor ports?"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by Mariane on 2011-06-09
I quote from: 
[https://wiki.ubuntu.com/X/Config/Resolution/#How%20to%20setup%20a%20dual%20monitor](https://wiki.ubuntu.com/X/Config/Resolution/#How%20to%20setup%20a%20dual%20monitor)
So people can see what I'm talking about

I need these names to use xrandr.

```

Intel driver - UMS names:
VGA - Analog VGA output
LVDS - Laptop panel
DP1 - DisplayPort output
TV - Integrated TV output
TMDS-1 - First DVI SDVO output
TMDS-2 - Second DVI SDVO output 

Intel driver - KMS names: 
LVDS1 - Laptop panel
VGA1 - Analog VGA output
DVI1 - Digital video output 

radeon driver names:
VGA-0 - Analog VGA output
LVDS - Laptop panel
S-video - Integrated TV output
DVI-0 - DVI output 

```

Mariane

---

### Post by Grenage on 2011-06-09
I don't believe the nvidia drivers support randr; if you have a card installed, you can type this to list ports:

```
xrandr -q
```

It may have changed recently; I will no doubt be corrected if this is the case.

---

### Post by Mariane on 2011-06-09
```
xrandr -q
```

only gives information about my laptop screen. I can get information about the second monitor by typing: 

```
xrandr --screen 1
```

But I cannot use the --output option to do anything with my second monitor because --output has to be followed by the name of the external monitor. For example: 

```
xrandr --output default
```

refers to the laptop screen. 

If xrandr does not work with nvidia cards, what should I use instead please? 

Mariane

---

### Post by Grenage on 2011-06-09
I can only speak from personal experience, and I've only ever stuck with the proprietary Nvidia driver.  An xorg.conf has always been created for me, and I've tailored it with the nvidia-settings utility; if this is not installed, you can install it using Synaptic, or by typing:

```
sudo apt-get install nvida-settings
```

But you probably already know that much!

---

### Post by Mariane on 2011-06-09
Thank you Grenage. nvidia-settings detected the second monitor when I clicked on "Detect Displays" and saved the info to xorg.conf. 

But xrandr apparently does not read xorg.conf. I've been fighting with this problem for a week now, the second monitor functions badly under gnome (no dragging of a window from one display to the other) and under KDE it only displays the background picture, and it displays it twice. Once apparently in 1440x900 pixels, the resolution of the laptop screen, and another time in 1680x1050 pixels, the correct resolution for the external monitor. The first picture is covering the second one. I cannot take a screenshot, programs do not function in the second monitor, but I'll take a random picture and tile it like my two background pictures are tiled to show what I mean. 

I got a DELL monitor because I have a DELL laptop and I wanted to avoid incompatibility issues. Ironic, isn't it? 

Mariane

---

### Post by Mariane on 2011-06-09
Ooops, forgot the picture

---

### Post by Grenage on 2011-06-09
Are you using Unity, the default for 11.04, or a classic Gnome interface?  I have no current experience of KDE, so I won't get involved there!

I assume that you are using "Twinview" in nvidia-settings, as you'll need it for dragging windows across screens.  Is the second monitor always connected?  We could probably add some metamodes to the xorg, which would allow you to enable/disable screens with xrandr.

---

### Post by Mariane on 2011-06-13
> **Grenage said:**
> 
We could probably add some metamodes to the xorg, which would allow you to enable/disable screens with xrandr.

Sounds perfect. How can I do this, please? 

I'm using 10.10, Ubuntu setup with the KDE interface installed later. 

Mariane

---

### Post by Grenage on 2011-06-14
Hi again, sorry for the delayed reply; every now and then I am actually busy. ;)

Are you currently using the *twinview* setting?  We'll want to get the screen displaying properly before progressing.

---

