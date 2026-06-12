---
title: "Cursor jumps when two fingers applied to touchpad"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by ManiacMagee on 2009-09-07
Hi all,
I recently installed Jaunty on an Acer Aspire 5535-5452 with a SynPS/2 Synaptics Touchpad.  When the touchpad is touched in more than one place, the cursor jumps erratically.  I ran synclient and found that only one finger is detected at a time.  Judging by the x and y coordinates, the touchpad is rapidly switching which finger is detected.
Any ideas on how to fix this?  Perhaps there is a way to make the touchpad ignore events that would correspond to movements that are unrealistically fast?  I don't feel any real need to emulate multi-finger detection, but I would like to keep the cursor from jumping all over the screen.
Thanks.

---

### Post by ManiacMagee on 2009-09-07
I found a bug report that describes a similar problem.  
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/365943](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/365943)
The patches in [        xfree86-driver-synaptics - 0.99.3-2ubuntu5]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597256/+listing-archive-extra") helped a lot.  The cursor still jumps a bit, but it is manageable now as long as I have tapping disabled.

---

### Post by izziere on 2009-09-08
I have a similar problem, this is one of the drawbacks of touchpads.  My laptop touchpad is either extremely sensitive under Ubuntu or does not pick up pressing at all.

My suggestion is if the cursor jumps when you put two fingers on the touchpad, stop putting two fingers on the touchpad.  It worked for me...

---

### Post by GrandVizier on 2010-10-05
I just got an Acer Travelmate 8372T and am testing Lucid Lynx on it. Running into the same erratic mouse when using 2 fingers.

I have version 1.2.2-1ubuntu4 of xserver-xorg-input-synaptics installed.

I've been running into difficulties trying to install xfree86-driver-synaptics and considering how old it is, I'm wondering if its still applicable. (ie how did the erratic touchpad continue to be an any issue?)

---

### Post by kDDs on 2010-10-05
Chances are your touchpad supports multi touch, but as there is nothing set up for it to do when you apply to fingers, it moves the cursor around in the direction of both.

First, go to System > Preferences > Mouse and click on the touchpad tab and see if you can enable Two-Finger scrolling.

Failing that, try these commands in the terminal:

```

$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10

$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 6

$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1

$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 0

```

That should enable two-finger scrolling on most synaptic touchpads, and stop the erratic behavior (and allow you to scroll by dragging two fingers on the touchpad :popcorn: _

---

### Post by GrandVizier on 2010-10-07
thanks for the tips, but no success

the radio button for enabling two-finger scrolling in Preferences->Mouse was greyed-out

ran the 4 commands and still nothing - after running the commands, here is the output of xinput list-props
```
$ xinput list-props "SynPS/2 Synaptics TouchPad"
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (125):	1
	Device Accel Profile (241):	0
	Device Accel Constant Deceleration (242):	1.000000
	Device Accel Adaptive Deceleration (244):	1.000000
	Device Accel Velocity Scaling (245):	10.000000
	Synaptics Edges (246):	1752, 5192, 1620, 4236
	Synaptics Finger (247):	24, 29, 255
	Synaptics Tap Time (248):	180
	Synaptics Tap Move (249):	221
	Synaptics Tap Durations (250):	180, 180, 100
	Synaptics Tap FastTap (251):	0
	Synaptics Middle Button Timeout (252):	75
	Synaptics Two-Finger Pressure (253):	10
	Synaptics Two-Finger Width (254):	6
	Synaptics Scrolling Distance (255):	100, 100
	Synaptics Edge Scrolling (256):	1, 0, 0
	Synaptics Two-Finger Scrolling (257):	1, 0
	Synaptics Move Speed (258):	0.400000, 0.700000, 0.009952, 40.000000
	Synaptics Edge Motion Pressure (259):	29, 159
	Synaptics Edge Motion Speed (260):	1, 401
	Synaptics Edge Motion Always (261):	0
	Synaptics Button Scrolling (262):	1, 1
	Synaptics Button Scrolling Repeat (263):	1, 1
	Synaptics Button Scrolling Time (264):	100
	Synaptics Off (265):	0
	Synaptics Guestmouse Off (266):	0
	Synaptics Locked Drags (267):	0
	Synaptics Locked Drags Timeout (268):	5000
	Synaptics Tap Action (269):	2, 3, 0, 0, 1, 3, 2
	Synaptics Click Action (270):	1, 1, 1
	Synaptics Circular Scrolling (271):	0
	Synaptics Circular Scrolling Distance (272):	0.100000
	Synaptics Circular Scrolling Trigger (273):	0
	Synaptics Circular Pad (274):	0
	Synaptics Palm Detection (275):	0
	Synaptics Palm Dimensions (276):	10, 199
	Synaptics Coasting Speed (277):	0.000000
	Synaptics Pressure Motion (278):	29, 159
	Synaptics Pressure Motion Factor (279):	1.000000, 1.000000
	Synaptics Grab Event Device (280):	1
	Synaptics Gestures (281):	1
	Synaptics Capabilities (282):	1, 1, 1, 0, 0
	Synaptics Pad Resolution (283):	139, 62
	Synaptics Area (284):	0, 0, 0, 0
	Synaptics Jumpy Cursor Threshold (285):	0
	Two-Finger Scrolling (530):	1
```

---

### Post by TheBestNameEver3 on 2010-11-10
No solution on this? I'm having the same problem?

---

### Post by DangerOnTheRanger on 2010-11-12
What worked for me was turning mouse sensitivity all the way down. I can finally play Teeworlds!

Anyway, go to **System > Preferences > Mouse**. Try turning "Sensitivity" all the way down.

That should do it!

---

