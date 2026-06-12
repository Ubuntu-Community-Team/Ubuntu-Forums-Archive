---
title: "Installing Intel Graphics Driver"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by darkfeline on 2009-04-05
My video card from lspci | grep VGA is
```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```

I don't think I have the Intel graphics driver installed because my xorg.conf file is

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I want to install the graphics driver, but I'm not sure where to start.  Help?

---

### Post by asmoore82 on 2009-04-06
With Intel, you've already got it.

From what I gather, Intel has contributed heavily to the advancement of the built-in Open Source drivers in recent years.
Not seeing any driver configuration in the "xorg.conf" file is due to the advancements there towards full auto-configuration.

To verify which driver is being auto-loaded for your Intel VGA and to see it's capabilities, you could run:
```
grep -i driver /var/log/Xorg.0.log
xrandr -v
xrandr
```

---

### Post by slughappy1 on 2009-04-06
Are you having display problems? Is that why you want to install drivers? Or is having your xorg.conf empty the reason?

---

### Post by 84loops on 2009-04-07
My xorg.conf file is the same way. Compiz does work it's just a little slow when I min or max a window. Also when I need to turn compiz off when I watch a video cause it causes it to pause and act weird. I think I need to uninstall the i810 driver.

---

### Post by skymera on 2009-04-07
The Intel graphics chips are really weak and Compiz will struggle at the more graphic intense animations.

I think there are two drivers for Intel:
i810 and Intel

When i had an intel chipset, i used Intel driver opposed to i810

---

### Post by slughappy1 on 2009-04-08
I could be wrong, I don't think I am though. The Intel driver is the new one that actually works, and is i810 is depreciated.... I think

---

### Post by riza hylviu on 2009-04-08
Save a copy of your xorg.conf so you can restore it if needed, and try some different configurations. My hp laptop has an intel graphics card and i use this configuration

        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 04)"
        Driver          "Intel"
It seems to work, try this with your configuration, puting your card name instead . But intel drivers are open so maybe it is already well configured.

---

### Post by slughappy1 on 2009-04-09
I would also say backup your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11xorg.conf.backup
```
 
Then try to uninstall the i810 driver and install the Intel driver. 
```
sudo apt-get remove xserver-xorg-video-i810 && sudo apt-get install xserver-xorg-video-intel

```

I would also say try and delete or clear the information out of the xorg.conf. On my laptop I literally do not even have an xorg.conf. I let HAL and dbus detect all of my hardware and preload all the drivers. Everything works perfectly and I don't need the xorg.conf, so I didn't need to deal with it at all :-)

---

### Post by Nepherte on 2009-04-09
> **skymera said:**
> The Intel graphics chips are really weak and Compiz will struggle at the more graphic intense animations.
The chip itself is not the issue. The Intel drivers don't work well with xorg 1.5

---

### Post by Jakey_TheSnake on 2009-04-09
You can see/select your graphics driver with a GUI using the:

```
displayconfig-gtk
```

command in the terminal.

---

