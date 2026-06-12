---
title: "Installing NVIDIA driver problem"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Brumm3l on 2009-09-03
This week I decided to have a go at installing Ubuntu 9.04. The installation went just fine and the system works, but when I tried to install the driver for the video card things went wrong.

The installation of the driver itself seems to work just fine, after that it say I need to reboot. When I reboot the ubuntu logo and the 'loading-bar' appear and when it's loaded and you would expect the login screen, my screen goes all black instead and the system doesn't seem to react on any commands.

I've tried installing the driver using envyng aswell, with the result.

The card is an AOpen Aeolus TI4200 8X-DVC1288(N) (AGP card), my screen is a 21.6" Samsung, running on 1680x1050.

Any help would be appreciated :)

---

### Post by nhasian on 2009-09-03
did you just enable the proprietary nvidia driver from system->administration->hardware drivers?  or did you download the driver directly from nvidia and try to install it yourself?

---

### Post by Brumm3l on 2009-09-03
I tried both options, with the same result: the black screen.

---

### Post by nhasian on 2009-09-03
just to confirm what graphics card you have:

```
lshw -C display
```

the package nvidia-glx-96 is compatible with the nvidia GeForce4 Ti 4200

```
sudo apt-get install nvidia-glx-96
```

---

### Post by Brumm3l on 2009-09-03
Thanks. I'm at the office right now, but will give it a go when I get back home.

---

### Post by gradinaruvasile on 2009-09-03
Did u try this driver?

[http://www.nvidia.com/object/linux_display_ia32_96.43.13.html](http://www.nvidia.com/object/linux_display_ia32_96.43.13.html)

---

### Post by Brumm3l on 2009-09-03
Yes, that's the driver I tried. I also found the .10 driver somewhere and installed that, but no result.

Should I uninstall the driver I currently got, although it's inactive, before installing the new one? And if I should, what commands should I use?

---

### Post by gradinaruvasile on 2009-09-03
> **Brumm3l said:**
> Yes, that's the driver I tried. I also found the .10 driver somewhere and installed that, but no result.

Should I uninstall the driver I currently got, although it's inactive, before installing the new one? And if I should, what commands should I use?

ABSOLUTELY. Uninstall everything. Uninstalling the Nvidia drivers from the site is done by:

```
sudo /path/to/driver/NVdiadrivername --uninstall
```
Then sudo dpkg-reconfigure xserver-xorg.

Also the best thing is to do the installation from recovery mode/root prompt.

---

### Post by Brumm3l on 2009-09-03
> **gradinaruvasile said:**
> Also the best thing is to do the installation from recovery mode/root prompt.

Do you know which option I should select in the recovery mode?

---

### Post by gradinaruvasile on 2009-09-03
> **Brumm3l said:**
> Do you know which option I should select in the recovery mode?

Recovery mode and from the drop down list root prompt. It is listed lower i think.

---

### Post by Brumm3l on 2009-09-03
Thanks for the help so far. As I posted earlier, I can't try it right now, but will do once I get back home.

Instead of uninstalling the driver, would a fresh install of Ubuntu have the same effect?

---

### Post by gradinaruvasile on 2009-09-03
Thats up to u, but i can tell u from experience that reinstalling from scratch doesnt always help.

---

### Post by Brumm3l on 2009-09-03
Thanks for that. I don't know the path to the driver, that's why I asked.

---

### Post by Brumm3l on 2009-09-04
> **nhasian said:**
> just to confirm what graphics card you have:

```
lshw -C display
```

the package nvidia-glx-96 is compatible with the nvidia GeForce4 Ti 4200

```
sudo apt-get install nvidia-glx-96
```

This seemed to work, but how do I check if the driver is installed properly?

I'd like to enable the 'normal' desktop visual effects: but that's not possble at the moment. Is the card not powerfull enough or could there be something else?

---

### Post by gradinaruvasile on 2009-09-04
> **Brumm3l said:**
> This seemed to work, but how do I check if the driver is installed properly?

I'd like to enable the 'normal' desktop visual effects: but that's not possble at the moment. Is the card not powerfull enough or could there be something else?

Its something else. U should be able to use full desktop effects.

Try in a terminal:

```
compiz --replace
```

What is the output of:

```
glxinfo | grep Open
```

---

### Post by Brumm3l on 2009-09-04
> **gradinaruvasile said:**
> Its something else. U should be able to use full desktop effects.

Try in a terminal:

```
compiz --replace
```

What should the result be?

> **gradinaruvasile said:**
> 
What is the output of:

```
glxinfo | grep Open
```

I'll post the output when I get home tonight...

---

### Post by gradinaruvasile on 2009-09-04
> **Brumm3l said:**
> What should the result be?


[COLOR="Red"]compiz --replace[/COLOR] is the command for enabling desktop effects

[COLOR="red"]glxinfo | grep Open[/COLOR] is a query about the vides system's glx extension (hardware acceleration properties sort of thingie). It has a loooong output, the grep command filters only the lines that have "Open" in them (from OpenGL)

Also u may try 

```
glxinfo | grep direct
```

If all is good, u should have "direct rendering: Yes" in its output - that basically means that u have hardware acceleration enabled.


[http://en.wikipedia.org/wiki/GLX]("http://en.wikipedia.org/wiki/GLX")

---

### Post by Brumm3l on 2009-09-04
Thanks for the information, I will post the results when I have them.

---

### Post by Brumm3l on 2009-10-08
Thanks for all the help. I never got the driver to work, but Ubuntu was running fine without it.

---

