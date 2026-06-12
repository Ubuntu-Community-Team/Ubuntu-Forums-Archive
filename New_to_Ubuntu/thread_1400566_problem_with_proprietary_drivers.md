---
title: "problem with proprietary drivers"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Hallucinate on 2010-02-07
okay i installed the ati proprietary drivers for my ati radeon hd 4650 diamond graphics card and then when i boot up it says that the refresh rate is too high like it says cannot display in a certain mode how do i edit xorg conf with out being inside of ubuntu can someon please help me

---

### Post by ikt on 2010-02-07
> **Hallucinate said:**
> okay i installed the ati proprietary drivers for my ati radeon hd 4650 diamond graphics card and then when i boot up it says that the refresh rate is too high like it says cannot display in a certain mode how do i edit xorg conf with out being inside of ubuntu can someon please help me

Does it go through to ubuntu or does it stop at the grub menu or does it not even reach the grub menu?

---

### Post by Hallucinate on 2010-02-07
It sets the refresh rate too high or too low for my monitor to view it i just need to know how to edit xorg.conf or w/e with out booting into it. Can i edit it with safety mode or w/e? It boots almost to the login screen. Once it hits the login screen it says cannot display this video mode in analog.

---

### Post by halitech on 2010-02-07
when it gets to the login screen and gives you the message about refresh too high, hit CTRL + ALT + F1 and log in with your username and password. then run
```
sudo nano /etc/X11/xorg.conf
```
and set the proper refresh for your monitor. then reboot again and it *should* work

---

### Post by Hallucinate on 2010-02-07
When i do that it brings me to a completely blank document. I can page down but it's still blank. I think i reset it with a command i typed earlier in an effort to fix it? dpkg-reconfigure xserver-xorg

---

### Post by halitech on 2010-02-07
did you type the command exactly as I typed it? if you did nano /etc/x11/xorg.conf it's not the same as /etc/X11/xorg.conf

---

### Post by Hallucinate on 2010-02-07
what would it be under i see monitor identifier etc

---

### Post by halitech on 2010-02-07
I do believe it would be under monitor. I only have to adjust the resolution on mine as it wants to display at 1600x1200 which my monitor doesn't support

here is mine:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Modes	"1280x1024" "1440x1050"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Hallucinate on 2010-02-07
> 

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Heres mine. Can you type it in where I need to edit it?


I booted into a live cd to paste that.

---

### Post by halitech on 2010-02-07
is that from the live cd or from the installed version? doesn't look like any xorg I've ever seen when using the ati drivers

---

### Post by Hallucinate on 2010-02-07
maybe i should reinstall ubuntu 9.04?

---

### Post by halitech on 2010-02-07
maybe try installing the actuall ATI drivers will work better

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English)

---

### Post by Hallucinate on 2010-02-07
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"


heres after enabling the proprietary drivers before reboot

---

