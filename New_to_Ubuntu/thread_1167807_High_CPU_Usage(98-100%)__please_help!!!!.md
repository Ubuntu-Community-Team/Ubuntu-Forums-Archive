---
title: "High CPU Usage(98-100%)  please help!!!!"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by linux_nood on 2009-05-23
hi there linux user i just intall ubuntu 9.04 and is running really bad i have a 98-100% CPU usage. i dont know much about linux ubuntu but i know that running that high off a CPU is bad.....like i said i dont know much about ubuntu but im sure someone can help....PLEASE HELP A NOOB OUT

---

### Post by Sef on 2009-05-23
Applications > Accessories > Terminal

the in the terminal type in this command:

```
top
``` copy and paste the results here.   Top will show you what is running and what is using so much of your CPU.

---

### Post by linux_nood on 2009-05-23
[IMG]file:///home/juan/Pictures/Screenshot.png[/IMG]i wont let let copy and paste

---

### Post by linux_nood on 2009-05-23
look at this screenshot

---

### Post by ajgreeny on 2009-05-23
x-org is your problem.  What video/graphics card do you have on the computer and which driver is it using?  Sort out that and you should have a better system.

Just out of interest have a look in your home for the hidden *.xsession.errors* file, which normally is only a few Kb.  If there are major xorg problems it may end up huge.

---

### Post by linux_nood on 2009-05-23
how would i be able to look at the driver that the graphics card is on....

---

### Post by linux_nood on 2009-05-23
does anyone have any idea of this problem,,,,,
i could really used some help...

---

### Post by Sarai the Geek on 2009-05-23
Type:

```
lspci | grep VGA
```in a terminal. It will spit out some information about your video card. Post that here!

By the way, copying and pasting in and out of a terminal is kind of annoying, you have to highlight the text then right click and select copy/paste: no ctrl-v or -c allowed.

---

### Post by linux_nood on 2009-05-23
this is what came out...... thanks for the help guys/ i really dont wanna go back to windows no more....

juan@juan-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
juan@juan-laptop:~$ lspci grep VGA
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
juan@juan-laptop:~$

---

### Post by Sarai the Geek on 2009-05-23
Haha, no one wants to go back to Windows, trust me!

Here's the pertinent part of that:
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
```

There are instructions [here]("https://help.ubuntu.com/community/RadeonDriver") regarding drivers for ATI Radeon cards.

---

### Post by linux_nood on 2009-05-23
so what u think is should do about all this codes

---

### Post by linux_nood on 2009-05-24
this is what i have done but i just dont know what to do next....:(
and my head is killing me now.....](*,)

---

### Post by linux_nood on 2009-05-24
no one has an idea of this ploblem

---

### Post by ibizatunes on 2009-05-24
have you install restricted driver
system > admin > hardware drives > enable ATI drivers

these are closed source drivers

---

### Post by Brinstar on 2009-05-24
System > Preferences > Appearance > Visual Effects

Make sure these are set to None

---

### Post by sandyd on 2009-05-24
accodring to [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)

fglx doesn't work properly

could you... 
```

cat /etc/X11/xorg.conf

```

im particularly interested in the "Devices" section

---

### Post by sandyd on 2009-05-24
im gonna have to edit it to make it include this...

```

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen		0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
	Option          "AccelMethod" "EXA"
	Option		"EXANoComposite" "false"
	Option		"FBTexPercent" "50"
	Option		"MigrationHeuristic" "greedy"
	Option		"DRI" "true"
	Option		"GARTSize"	"256"
	Option		"AGPMode" "4"
	Option		"Colortiling" "On"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen		0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
	Option "AIGLX" "true"
EndSection

Section "Extensions"
	Option  "Composite" "Enable"
EndSection

Section "DRI"
	Mode 0666
EndSection

```
except that i gotta change GARTSize to the amount of system ram he put aside for his card.

---

### Post by linux_nood on 2009-05-24
i check this and notthing was coming up there was just a blank screen....
system > admin > hardware drives > enable ATI drivers.

then i check the visual effect and the laptop is running a little better now...
System > Preferences > Appearance > Visual Effects

this is what comes up in code u gave me CARLEE
juan@juan-laptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
juan@juan-laptop:~$

---

### Post by linux_nood on 2009-05-24
i dont know if that looks good or not.....

---

### Post by X-Kent on 2009-06-07
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365775](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365775)
may this be your problem ?

---

