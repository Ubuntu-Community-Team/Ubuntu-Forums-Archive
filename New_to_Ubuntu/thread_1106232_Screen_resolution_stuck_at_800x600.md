---
title: "Screen resolution stuck at 800x600"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by vyco10 on 2009-03-25
FYI, I have the nVidia Corporation NV34 [GeForce FX 5200] graphics card. I am running Ubuntu Intrepid (8.10). I have done the System --> Administration --> Hardware Drivers "thing". All that does is make things worse and cause my monitor to go to an even lower resolution.

---

### Post by Ms_Angel_D on 2009-03-25
You should Go to System->Administration->Hardware Drivers it should give you the option to install the restricted driver for Nvidia. Don't forget to reboot after enabling the driver.

---

### Post by vyco10 on 2009-03-25
> **MetalHellsAngel said:**
> You should Go to System->Administration->Hardware Drivers it should give you the option to install the restricted driver for Nvidia. Don't forget to reboot after enabling the driver.

I'd already done that, and when I rebooted the screen resolution was even lower than before I'd installed the driver. That's where I get stuck.

---

### Post by mpsii on 2009-03-25
You have to modify your xorg.conf and put in the actual HorizSych and VertRefresh ranges to your monitor. For whatever reason, it will not autodetect. The following was on my GeForce4 MX 420 AGP card.

example, just using DPMS, in your xorg.conf file:

```
Section "Monitor"
Identifier "Monitor"
Option "DPMS" "true"
EndSection
```

or
example, using HorizSync and VertRefresh

```
Section "Monitor"
Identifier "Monitor"
HorizSync      60.0 - 77.0
VertRefresh    60.0 - 75.0
EndSection
```

or
example, combining the two (worked on my no-name crappy monitor)

```
Section "Monitor"
Identifier "Monitor"
HorizSync      60.0 - 77.0
VertRefresh    60.0 - 75.0
Option "DPMS" "true"
EndSection
```

---

### Post by vyco10 on 2009-03-26
> **mpsii said:**
> You have to modify your xorg.conf and put in the actual HorizSych and VertRefresh ranges to your monitor. For whatever reason, it will not autodetect. The following was on my GeForce4 MX 420 AGP card.

example, just using DPMS, in your xorg.conf file:

```
Section "Monitor"
Identifier "Monitor"
Option "DPMS" "true"
EndSection
```

or
example, using HorizSync and VertRefresh

```
Section "Monitor"
Identifier "Monitor"
HorizSync      60.0 - 77.0
VertRefresh    60.0 - 75.0
EndSection
```

or
example, combining the two (worked on my no-name crappy monitor)

```
Section "Monitor"
Identifier "Monitor"
HorizSync      60.0 - 77.0
VertRefresh    60.0 - 75.0
Option "DPMS" "true"
EndSection
```

You, sir, are the man (*or woman... if that be the case*) That fixed it. I've got my beloved 1024x768 screen rez back. :guitar:

Extra question: If I wanted a screen resolution a few steps higher than 1024x768, since I was able to get that in Windows XP, what would the HorizSync and VertRefresh be for that?

---

### Post by CatKiller on 2009-03-26
> **vyco10 said:**
> Extra question: If I wanted a screen resolution a few steps higher than 1024x768, since I was able to get that in Windows XP, what would the HorizSync and VertRefresh be for that?

It depends entirely on what your monitor can do. The reason you get low resolution when the values are not detected is because setting the values too high will damage a CRT monitor. Find the values for **your** monitor - either from the manual or from the monitor manufacturer's website - and put those in. Then you'll get all the resolutions and refresh rates that the people who made the monitor say that it can do. Don't just put in arbitrary values that you found on the Internet for someone else's monitor. Doing so would be a Bad Plan.

---

### Post by mpsii on 2009-03-26
To add to the above...

First try to set the resolution to higher than 1024x768 with the nvidia-settings or screen resolution tools.

Other than that, find out what your monitor can handle, then add the following to your xorg.conf in the Section "Screen" (the following is an example; I don't know what your monitor can handle):

```
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

```

---

### Post by vyco10 on 2009-03-26
The monitor I have is a Dell E773c monitor. The manual had the following under it's resolution information:

**Resolution**

[INDENT]Horizontal scan range - 30 kHz to 70 kHz (automatic)
Vertical scan range - 50 Hz to 160 Hz (automatic)

Optimal preset resolution - 1024 x 768 at 75 Hz
Highest preset resolution - 1024 x 768 at 85 Hz
Highest addressable resolution* - 1280 x 1024 at 60 Hz

* Addressable means the monitor will sync up to this mode.  However, Dell does not guarantee the image will be sized and centered correctly.
Dell guarantees image size and centering for all preset modes listed in the following table.[/INDENT]

So, I can go higher than 1024x768, but it's not a guarantee that it will look right.

Btw, for information purposes this is the Dell guaranteed image size and centering, just for 1024x768 and higher:

[INDENT]VESA, 1024 x 768 - Horiz. 68.7, Vert. 85.0, Pixel Clock 94.5, Sync +/+
VESA, 1152 x 864 - Horiz. 67.5, Vert. 75.0, Pixel Clock 108.0, Sync +/+[/INDENT]

So help me out, just so I'm safe. What do I enter for 1152x864 resolution if I wanted to have that option?

**EDIT**: Nevermind about what I need to enter for that resolution. I went into NVIDIA X server settings and was able to change it there.

Thanks for the help, guys.

---

