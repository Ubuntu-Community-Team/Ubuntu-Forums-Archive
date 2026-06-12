---
title: "how to install 9.10 with an old display?"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Rumtscho on 2010-01-24
Hi, 

I want to make a clean install of 9.10. Popped the CD, but my (old model TFT) display only said "Input signal out of range". So I made a backup of my xorg.conf and made a fresh install from the alternate installer CD. On boot, I only see the same warning on the blank screen. How can I get the PC to work? Or is it impossible? I guess it is only a matter of changing the values of refresh rates and resolution to something supported by the display, or am I wrong? 

Some options which won't work: I cannot hook up another monitor, because I don't have any. I cannot hook up the HDD to another system and replace the xorg.conf, because I don't have another desktop PC and my laptop doesn't have free ATA connectors. I cannot remote into the PC, because I don't have a network (and even if I were to buy cables and try to set up one, I couldn't change the settings on the PC without display). 

So is there a way to repair that? Maybe some way to force the system to boot in minimal graphics mode for long enough to replace the conf file? Or should I just reinstall 9.04? If I install 9.04 first and use the upgrade feature from within the update manager, will I still have the correct settings, or will 9.10 overwrite them? 

If this matters, my display is a Fujitsu Siemens Scaleoview C17-6, and my videocard is a GeForce 7600. That worked under 9.04 with following parameters: 

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync 30-81
	VertRefresh 55-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		   Depth 24
		   Modes "1280x1024_60"
	EndSubSection
EndSection

```

---

### Post by cariboo on 2010-01-24
You should be able to start in recovery mode. once at the prompt type:

```
nvidia-xconfig
```

This command will create a new /etc/X11/xorg.conf file. Check the refresh rates, as you may need to edit them before rebooting.

---

### Post by NCLI on 2010-01-24
To edit the file nvidia-xconfig creates for you, type "sudo nano /etc/X11/xorg.conf"

---

### Post by Rumtscho on 2010-01-24
Thank you for the answers, but I still couldn't get the PC to run in normal mode. 

I started in recovery mode and typed in a new xorg.conf identical to my backup, except for the driver - I have to use 'nv' because I cannot install the usual nvidia-glx-195. Now when I start the PC, the display gets a signal. The system boots to following screen: 

```

Ubuntu 9.10 Steinbeck tty1

Steinbeck login: _
``` 

This flashes visibly, at about 2 Hz. When I try to type in a login, it only gets the signal from every second or third keystroke. 

I looked at the Xorg.0.log, here are the parts I think are relevant: 

```

(==) No Layout section. Using the first Screen section. 
(**) |-->Screen "Default Screen" (0)
(**) |   |--> Monitor "Configured Monitor" 
(**) |   |--> Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices 

```
Then it says something about fonts and other things. Then
```

(--) PCI:*(o:1:0:0) 10de:02e1:nVidia Corporation G73 [GeForce 7600 GS$

```
then other things, then
```

"glx" will be loaded. This was enabled by default and also specified in th$

```
then it loads glx and some other modules, and then comes the nv module: 
```

(II) Module nv: vendor="X.Org Foundation"
        compiled for 1.6.3, module version = 2.1.14
        Module class: X.Org Video Driver 
        ABI class: X.Org Video Driver, version 5.0 
(II) NV: driver for NVIDIA chipsets: {here comes a list starting at RIVA
 128 and listing what seems to be every single nvidia model since; mine 
is also in the list}
(II) Primary Device is: PCI 01@00:00:0
(EE) No devices detected. 

Fatal server error: no screens found

```

and there the log ends with advice to look for help at the X.Org Foundation wiki. 

1. Does anybody know what happens here and why? 
2. I'd like to install the proprietary nvidia driver. But my only way to get an internet connection to this PC is over wireless. As there is no nice GUI tool in recovery mode, I tried configuring wpasupplicant, but all I get is the message "Association request to the driver failed". How do I install the nvidia driver without an internet connection on the PC itself? 
3. I wanted to copy my xorg.conf file and my log file to a flash drive so I can post the content here using my laptop. But I don't know how to do it in recovery mode. I think that the flash drive gets mounted, because when I plug it in, some lines appear in the console, and then there is a /dev/sdb and /dev/sdb1. But when I try to copy a file there, I get the message "cp: accessing '/dev/sdb/xorglogfile1': Not a directory". I guess that I'll have to use the flash drive for installing a nvidia driver downloaded from the laptop. So the third question: in recovery mode, how do I access a flash drive?

---

