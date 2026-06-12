---
title: "Dual Monitor Issues - Ubuntu 9.10 - Intel 945G"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by d0ti5 on 2009-11-11
OK, you can beat me, I am ready for it, I fail.  But I can not figure this out for the life of me.

I have a Lenovo T-60 with 3GB memory, dual 100 GB hard drives running Ubuntu 9.10.  This is an Intel Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller.  I have an IBM P260 monitor.

From the standpoint of physical positioning, they are side by side:
[IMG]http://home.comcast.net/~d0ti5/images/reality.png[/IMG] 
No matter what I try, this is what they do:
[IMG]http://home.comcast.net/~d0ti5/images/whatitdoes.png[/IMG]
Additionally, the maximized position for programs is on the "lower" monitor, so I can not maximize one program on the laptop and another on the CRT, nor can I move the program back to the laptop once set on the CRT.

Use of xrandr positioning (or the GUI grandr or Display Settings) to put them side by side causes correct positioning, but both screens are black except for a 2 - 3 pixel wide line on the left of the laptop display.  

While convinced of PEBCAK as the source, I would sure like to fix this.  Some pertinent info:

----------------------------------------------------------

lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

----------------------------------------------------------

lshw -C Display | grep product:
product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller

----------------------------------------------------------

xrandr
Screen 0: minimum 320 x 200, current 1024 x 1536, maximum 4096 x 4096
VGA1 connected 1024x768+0+768 (normal left inverted right x axis y axis) 392mm x 294mm
   1024x768       85.0*+   75.1     75.0     70.1     60.0  
   1600x1200      85.0 +   85.0     75.0     70.0     65.0     60.0  
   2048x1536      75.0     60.0  
   1920x1440      85.0     75.0     60.0  
   1856x1392      75.0     60.0  
   1792x1344      75.0     60.0  
   1680x1050      84.9     74.9     69.9     60.0  
   1600x1024      60.2  
   1400x1050      85.0     74.8     70.0     60.0  
   1280x1024      85.0     75.0     60.0  
   1440x900       59.9  
   1280x960       85.0     60.0  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     75.0     72.8     75.0     60.0     59.9  
   720x400        85.0     70.1  
   640x400        85.1  
   640x350        85.1  
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 286mm x 214mm
   1024x768       60.0*+   85.0     75.0     70.1     60.0*    50.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 disconnected (normal left inverted right x axis y axis)

----------------------------------------------------------

xorg.conf:
Section "Device"
	Identifier	"Intel 945G"
	Driver		"intel"
	Option		"monitor-VGA" "VGA1"
	Option		"monitor-LVDS" "LVDS1"
EndSection

Section "Monitor"
	Identifier	"VGA1"
	Option		"PreferredMode" "1024x768"
	Option		"Position" "1024 0"
	Option		"RightOf" "LVDS1"
EndSection

Section "Monitor"
	Identifier	"LVDS1"
	Option		"PreferredMode" "1024x768"
	Option		"Position" "0 0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Intel Corporation 945G Integrated Graphics Controller"
	Subsection	"Display"
		Virtual 	4096 4096
	EndSubSection
EndSection

----------------------------------------------------------

Can someone help a brother?

---

### Post by ABCC on 2009-11-20
Everything looks good but it doesn't work, I know the pain...

Have you tried running without an xorg.conf yet? The latest Xorg is smart enough to do without, so renaming it and restarting X might solve things. 

Other than that... dunno, what xrandr command are you using? Here's what I usually run when I set my screen side by side:


```
xrandr --output LVDS1 --auto --left-of --output VGA1 --auto
```

hth,

ABCC

---

### Post by sbrbot on 2009-12-17
In section "Screen" you do have: 
Monitor "Configured Monitor"

There's no monitor identified by "Configured Monitor" tag, just "VGA1" and "LVDS1".

Also Device "Intel Corporation 945G Integrated Graphics Controller" in Screen should correspond with driver identifier defined in "Device" section.

---

### Post by stojo on 2010-02-06
Lol... Same problem, same hardware ...

---

### Post by netgunner on 2010-03-03
Sorry but i am a noob, well been playing for a while and now i need help. Same issue cant get my box to run 2 displays like in windows 7. here is what xrandr gives me:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0  
   1152x864       75.0  
   1024x768       75.1*    60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       59.9 +
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)

really don't understand have followed several post but every time i try my box goes black 

any help PLEASE!!!!!!!!!!!!!!!!!!!!

---

