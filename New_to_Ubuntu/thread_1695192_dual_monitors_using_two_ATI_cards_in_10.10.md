---
title: "dual monitors using two ATI cards in 10.10"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by guarnibl on 2011-02-25
I've a 4350 and 5850 installed on my system. One monitor on each (upgrading to quad display in the next week). How do I get Ubuntu to work with both cards in 10.10? Only one screen is working at the moment.

```


brett@guarnibl:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Device 689e
01:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
02:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
brett@guarnibl:~$ 

```

```

brett@guarnibl:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series  
OpenGL version string: 4.0.10237 Compatibility Profile Context

```

```

brett@guarnibl:~$ perl -n0077 -e 'print "Using driver $1 v$3 by $2.\n" while /Module (radeon|fglrx|intel|nvidia|nv|vesa): vendor="([^"]+)"\n.*version = (\S+)/img;' /var/log/Xorg.${DISPLAY:1:1}.log
Using driver fglrx v8.78.30 by FireGL - ATI Technologies Inc..

```

```


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```


```


brett@guarnibl:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       75.0     60.0  
   1152x864       75.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)
brett@guarnibl:~$ 

```

---

### Post by guarnibl on 2011-02-25
still not working, but i have both adapters showing in fglrxinfo now. thoughts? still doesn't show in amdccc.

```

brett@guarnibl:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series  
OpenGL version string: 4.0.10237 Compatibility Profile Context

display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4300/4500 Series
OpenGL version string: 3.3.10237 Compatibility Profile Context

```


```


brett@guarnibl:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
	Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-1"
	Screen         "aticonfig-Screen[1]-1" RightOf "aticonfig-Screen[1]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-0"
	Device     "aticonfig-Device[1]-0"
	Monitor    "aticonfig-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-1"
	Device     "aticonfig-Device[1]-1"
	Monitor    "aticonfig-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Ben Page on 2011-02-25
Just a hint if you did not do it. Install the proprietary drivers from AMD/ATI, you should get a prompt that proprietary drivers are available for your hardware.

Are you sure that what are you trying to do is possible? Have you managed to get these cards running in another OS?

---

### Post by guarnibl on 2011-02-25
> **Ben Page said:**
> Just a hint if you did not do it. Install the proprietary drivers from AMD/ATI, you should get a prompt that proprietary drivers are available for your hardware.

Are you sure that what are you trying to do is possible? Have you managed to get these cards running in another OS?

I'm using the proprietary drivers already as recommended.. never installed anything else.

Yes, it's working on Windows.. I'm dual booting :)

---

### Post by guarnibl on 2011-02-25
Got it :) 

Ran from console "sudo X -configure" and restarted.

---

