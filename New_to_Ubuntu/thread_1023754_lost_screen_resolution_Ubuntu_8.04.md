---
title: "lost screen resolution Ubuntu 8.04"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by mike_plays_golf on 2008-12-28
As most users say, I am really new to Ubuntu and Linux.

I have an old Jetway V2DP motherboard that had Windows 2000 on it and I wanted to play with Ubuntu 8.04.  Downloaded a disc, did a checksum verification on it and even did a disc test before installing.  Installed OK and everything worked fine (i.e., my MB manual says it has a UniChrome integrated VGA) as I had a screen resolution of 1280*1024.  The update manager pooped up on the top tool bar and said I had two updates.  I did these and rebooted and now my screen resolution is 800*600.  I did the update manager again and it installed ~200 updates and I still have the same problem.  I read several threads about updating /etc/X11/xorg.conf and tried several items with no luck.  I see through Synaptic there is a UniChrome driver and it is installed.

I have the following:
```
mike@mach:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

```

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

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
	SubSection	"Display"
		Modes	"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```


:confused::confused:Any help would be greatly appreciated!!:confused::confused:

---

### Post by wolfen69 on 2008-12-28
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x or reboot.

---

### Post by unutbu on 2008-12-28
Please post the output of 
```

ls -l /etc/X11
```

---

### Post by mike_plays_golf on 2008-12-28
Forgot to mention that I tried that and got this message:
```
mike@mach:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for mike: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081228102810

```

Restarted and still not able to change the resolution.

---

### Post by mike_plays_golf on 2008-12-28
```
mike@mach:~$ ls -l /etc/X11
total 100
drwxr-xr-x 2 root root  4096 2008-07-02 06:30 app-defaults
drwxr-xr-x 2 root root  4096 2008-07-02 06:32 cursors
-rw-r--r-- 1 root root    14 2008-07-02 06:29 default-display-manager
drwxr-xr-x 6 root root  4096 2008-07-02 06:21 fonts
-rw-r--r-- 1 root root 17394 2008-05-13 20:10 rgb.txt
lrwxrwxrwx 1 root root    13 2008-12-27 16:11 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2008-07-02 06:26 xinit
drwxr-xr-x 2 root root  4096 2008-12-28 08:19 xkb
-rw-r--r-- 1 root root  1293 2008-12-28 10:39 xorg.conf
-rw-r--r-- 1 root root  1225 2008-12-28 10:28 xorg.conf~
-rw-r--r-- 1 root root  1225 2008-12-28 09:10 xorg.conf.20081228091013
-rw-r--r-- 1 root root  1225 2008-12-28 09:10 xorg.conf.20081228091040
-rw-r--r-- 1 root root  1225 2008-12-28 09:10 xorg.conf.20081228091057
-rw-r--r-- 1 root root  1407 2008-12-28 09:29 xorg.conf.20081228092929
-rw-r--r-- 1 root root  1225 2008-12-28 09:50 xorg.conf.20081228095021
-rw-r--r-- 1 root root  1293 2008-12-28 10:28 xorg.conf.20081228102810
drwxr-xr-x 2 root root  4096 2008-07-02 06:18 Xresources
drwxr-xr-x 2 root root  4096 2008-12-28 10:17 xserver
-rwxr-xr-x 1 root root  3730 2008-05-13 20:10 Xsession
drwxr-xr-x 2 root root  4096 2008-07-02 06:35 Xsession.d
-rw-r--r-- 1 root root   265 2008-05-13 20:10 Xsession.options
-rw------- 1 root root   614 2008-07-02 06:18 Xwrapper.config

```

---

### Post by mapes12 on 2008-12-28
Right click Applications>Edit Menu. From the GUI select Other in L/H column then Screen and Graphics in R/H column. You may have to reboot but then go Applications>Other>Screen and Graphics. When the GUI opens then select your hardware from the tabs then set your screen res.

This worked for me in 8.04 with a similar problem.

---

### Post by linux_tech on 2008-12-28
what is output of ```
xrandr
```
this should give you available resolutions
what resolution do you want?

make a bakup of your xorg.conf
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak

you can either try using xrandr to adjust resolution (if you have a resolution listed)

ie. [code]xrandr -s 1024x768
```

or you can use ```
gnome gksu displayconfig-gtk

```

or you can copy over a previous xorg.conf to replace the current xorg.conf
that you've already made a backup of 

for example 
```
cp /etc/X11/xorg.conf.20081228091013 /etc/X11/xorg.conf
```

---

### Post by mike_plays_golf on 2009-01-01
Thanks for all the help, I ended up reinstalling Ubuntu.  After that I could change the monitor via mapes12 suggestion and then was able to change the resolution.  Strange....

---

