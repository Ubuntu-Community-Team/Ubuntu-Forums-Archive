---
title: "How can I get back my normal resolution (1280x1024)"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by Nikola Georgiev on 2011-03-14
After a switch between users and an update, I got an error message  "couldn't set back monitor/resolution settings" (or something like  that). Now I can't get back my normal resolution (1280x1024), because it disappeared from System -> Preferences -> Monitors as an option. I tried  editing that xorg.conf file (it was empty), but I wasn't able (I am an absolute  beginner :grin:).

Edit: My Graphics card is 
```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```
My monitor is Acer Monitor AL1716.





.

---

### Post by Grenage on 2011-03-14
> **Nikola Georgiev said:**
> After a switch between users and an update, I got an error message  "couldn't set back monitor/resolution settings" (or something like  that). Now I can't get back my normal resolution (1280x1024), because it disappeared from System -> Preferences -> Monitors as an option. I tried  editing that xorg.conf file, but I wasn't able (I am an absolute  beginner :grin:).

Hi there,

Do you have an Nvidia/ATI graphics card, or an on-board graphics card such as Intel?  If unsure, run this from a terminal, and paste the results:

```
lspci | grep VGA
```

Could you post what you've got in your xorg.conf file?  Your monitor make and model can't hurt, either.

---

### Post by Nikola Georgiev on 2011-03-14
> **Grenage said:**
> Hi there,

Do you have an Nvidia/ATI graphics card, or an on-board graphics card such as Intel?  If unsure, run this from a terminal, and paste the results:

```
lspci | grep VGA
```Could you post what you've got in your xorg.conf file?  Your monitor make and model can't hurt, either.

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
The xorg.conf file was empty. My monitor is Acer Monitor AL1716.

---

### Post by Morridin on 2011-03-14
Double check for any available drivers and such under the Administration tab.

---

### Post by Nikola Georgiev on 2011-03-14
> **Morridin said:**
> Double check for any available drivers and such under the Administration tab.
If you mean:
System -> Administration -> Hardware drivers 
There is a message there:
"No proprietary drivers are in use on this system."

---

### Post by Grenage on 2011-03-15
> **Nikola Georgiev said:**
> 00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
The xorg.conf file was empty. My monitor is Acer Monitor AL1716.

Try using the following for your xorg.conf.  First you'll need to edit it using root privileges:

```
gksu gedit /etc/X11/xorg.conf
```

Then paste in the details, save, and either restart X or reboot:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "ACER"
	ModelName "AL1716"
	HorizSync 30 - 80
	VertRefresh 55 - 75
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 82945G"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

If that doesn't work, add the following line below *VertRefresh*:

```
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

Then either restart X, or reboot.

---

### Post by Nikola Georgiev on 2011-03-15
> **Grenage said:**
> Try using the following for your xorg.conf.  First you'll need to edit it using root privileges:

```
gksu gedit /etc/X11/xorg.conf
```Then paste in the details, save, and either restart X or reboot:

```
Section "Monitor"
    Identifier "Monitor0"
    VendorName "ACER"
    ModelName "AL1716"
    HorizSync 30 - 80
    VertRefresh 55 - 75
EndSection

Section "Device"
    Identifier "Device0"
    Driver "intel"
    VendorName "Intel 82945G"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1280x1024"
    EndSubSection
EndSection
```If that doesn't work, add the following line below *VertRefresh*:

```
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```Then either restart X, or reboot.

It worked.
Big thanks, mate!

---

### Post by Grenage on 2011-03-15
Peachy, glad to hear it!

---

