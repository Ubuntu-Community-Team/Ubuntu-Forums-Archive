---
title: "Screen too small"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by The Eight-Bit Link on 2010-05-16
my Screen is too small for comfort. It is 800x600, and I know it can go to 1024xsomething. I don't really care for screen speed, just want it larger.

---

### Post by 4Orbs on 2010-05-16
I suggest going to Applications>> System>> Hardware Drivers and activate the recommended driver for your video card (if there is a driver available for your card). After you activate and reboot, the screen resolution should have readjusted automatically to your monitor.

---

### Post by The Eight-Bit Link on 2010-05-16
What if there is no reccommended drivers for it?
Any way to force it?

---

### Post by 4Orbs on 2010-05-16
You can open System>> XFCE 4 Settings Mgr and click on Display and that will show your screen resolutions choices. But that might only show 800x600 as the highest resolution. Let us know.

EDIT: Sorry it should be Applications>> Settings>> xfce 4 Settings Mgr

---

### Post by halitech on 2010-05-16
What video card do you have? Is this a laptop or a desktop?

open a terminal and run
```
lspci
```
and post the output here

I did some searching and it seems like you have an Intel onboard video on a Dell 2500 laptop.Try this:

open a terminal and run
```
sudo touch /etc/X11/xorg.conf
```
```
gksudo mousepad /etc/X11/xorg.conf
```
add the following info and reboot
```
Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS" "true"
	HorizSync	30.0-60.0
	VertRefresh	50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
			Depth		24
			Modes		"1024x768" "800x600"
	EndSubSection

EndSection
```

---

### Post by The Eight-Bit Link on 2010-05-17
Output from the lspci```

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
01:03.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
01:03.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
01:0b.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
02:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
02:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)
```

---

### Post by 4Orbs on 2010-05-17
Those two terminal commands by halitech contain typo errors. They should read this way:
```
sudo touch /etc/X11/xorg.conf
```

```
gksudo mousepad /etc/X11/xorg.conf
```

---

### Post by halitech on 2010-05-17
> **4Orbs said:**
> Those two terminal commands by halitech contain typo errors. They should read this way:
```
sudo touch /etc/X11/xorg.conf
```

```
gksudo mousepad /etc/X11/xorg.conf
```

thanks for picking that up, guess thats what happens when I type too fast :(

---

### Post by The Eight-Bit Link on 2010-05-17
it says it can't touch the file?
would it be of any help to tell you i'm  running 10.04.

---

### Post by searchesend on 2010-05-17
I'm using Xubuntu 10.04 on a Dell Inspiron 2500 and these instructions worked fine - thanks a lot!
I don't know why you can't touch the file Eight-Bit? I just entered the commands into the terminal and entered my password and the file opened?

---

### Post by The Eight-Bit Link on 2010-05-17
Oh boy. I think I have a bigger problem. Maybe it.. deleted it?
Ugh, here we go again.

---

### Post by halitech on 2010-05-18
the touch command simply creates the file, it doesn't open the file of anything. If you enter the command and nothing happens then it completed successfully. The second command will open the file.

---

