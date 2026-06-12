---
title: "s-video output on compaq r4000 not working"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by bigredphil on 2011-07-16
Hi i'm having trouble getting my s-video output to work on ubuntu 10.10. It won't detect the output at all. I think my graphics card is a ATI Radeon Xpress 200M. Any suggestions?

---

### Post by realzippy on 2011-07-16
Welcome!
Maybe this helps:
[http://ubuntuforums.org/showthread.php?t=1332157](http://ubuntuforums.org/showthread.php?t=1332157)

---

### Post by bigredphil on 2011-07-17
thanks for this...i can't get it to work though. When I run s-video on it just changes my screen to a lower resolution and I cant overwrite the original xorg.conf file with new one.

---

### Post by realzippy on 2011-07-17
*I cant overwrite the original xorg.conf file with new one*

...how did you try?
Please specify;post terminal output.

---

### Post by bigredphil on 2011-07-17
I tried to copy and paste the xorg.conf file from the link you sent me to overwrite the xorg.conf file in /usr/share/doc/xserver-xorg-video-nouveau/examples...when I did this I got the message "Error moving file: Permission denied" Applogies if i'm going about this copletly the wrong way, I'm a newbie.

---

### Post by realzippy on 2011-07-17
Yeah,you are completely wrong.No problem,we are in beginner's talk.

Let's start step by step:

Open terminal,run

```
xrandr -q
```

...post the output please.

---

### Post by bigredphil on 2011-07-17
phil@phil-Presario-R4100-EE997EA-ABU:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 289mm x 2100mm
   1280x800       60.1*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)
   800x600        59.9

---

### Post by realzippy on 2011-07-17
**Edit.**
Crossposting/editing
Ok,wait a minute...

---

### Post by realzippy on 2011-07-17
Ok,
now try that xorg.conf from that link:
Open terminal,run

```
gksudo gedit /etc/X11/xorg.conf
```

An empty file pops up.
(If file should not be empty,stop here and post it's content!)
Paste into that empty file:

```
Section "Monitor"
	Identifier "InternalLCD"
	Option "DPMS"
EndSection

Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Depth          24
	EndSubSection
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Device"
	Identifier "Configured Video Device"
	Driver "radeon"
	Option	"SWcursor" "off"
	Option "AccelMethod" "EXA"
	Option "AccelDFS" "1"
	Option "RenderAccel" "true"
	Option "BackingStore" "true"
	Option "EnablePageFlip" "true"
	Option "ColorTiling" "true"
	Option	"EnableDepthMoves" "true"
# TV Section
	Option "TVStandard" "ntsc"
	Option "TVDACLoadDetect" "TRUE"
EndSection

```

close file saving changes.
Reboot.
If booting does not work,press "shift" during boot,
start "recovery" mode and start "low graphics mode".
If reboot works,connect your TV to the s-video output,
power it on and run
```
xrandr -q
``` 
again.Post again the output.

---

### Post by bigredphil on 2011-07-17
ok so the file was empty and the computer rebootted fine. the s-video output is connected an this is what i get


phil@phil-Presario-R4100-EE997EA-ABU:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 289mm x 2100mm
   1280x800       60.1*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)
   800x600        59.9

---

### Post by realzippy on 2011-07-17
Your TV connected and powered on?

Btw,where is your location?
Asking because need to know if you have PAL or NTSC video standart...


**Edit:**

Which resolution does the TV support?

---

### Post by bigredphil on 2011-07-17
yeah the tv is connected and powered on. it's display resolution is 854 x 480 pixels. The tv and laptop are defiantly compatible, I used them both together when i was running windows by pressing fn + f4. I'm in ireland so i would be PAL

---

### Post by realzippy on 2011-07-17
Problem seems to be that TV is not recognised by xrandr..:
*S-video disconnected*
although TV is connected and powered on.


Anyway,open xorg.conf again:

```
gksudo gedit /etc/X11/xorg.conf
```

and change:
Option "TVStandard" "ntsc"
to
Option "TVStandard" "pal"
close file saving changes.
Reboot.
Doubt it changes something for the "disconnected" topic,
but again run
```
xrandr -q
```
to see.Also check if FN+ F4 "connects" the TV (s-video).
If s-video still disconnected,it might be this bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/573550](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/573550)
We can test igor's workaround then.

---

### Post by bigredphil on 2011-07-17
I've changed it from ntsc to pal and also tried fn + f4 and it still says s-video disconnected

---

### Post by realzippy on 2011-07-17
run
```
xrandr --output S-video --set load_detection 1
```
and
```
xrandr --output S-video --mode 800x600
```

..does anything happen?errors?

---

### Post by bigredphil on 2011-07-17
YES!! By running those two lines of code the image is appearing on the tv. Thanks!

---

### Post by bigredphil on 2011-07-17
Although when I try and play a video the video plays on the laptop but appears black on the tv...

---

### Post by realzippy on 2011-07-17
Also other windows or videos only?

---

### Post by bigredphil on 2011-07-17
other windows work fine, its just the video

---

### Post by realzippy on 2011-07-17
No idea,had to search a while..
Note,I am not in front of your machine.Don't have a S-video output
nor am I running an ATI video adapter (for a good reason  ;-) )...
All I can do for you is theoretically.
So forgive the stupid question,but:

Your main monitor (laptop) runs in 1280x800.
You open a video in a window,but when you "drag" it to the TV,
it becomes black?

Edit:
What happens when setting laptop's resolution to 800x600 before ?
```
xrandr -s 800x600
```
Video also is (gets) black ?

---

### Post by realzippy on 2011-07-19
...have you given up ?

---

### Post by bigredphil on 2011-07-22
essentially yes.....that computer has completely died on me.....s-video is the least of my concerns. thanks for your help!

---

