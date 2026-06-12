---
title: "3 finger swipe using synaptics trackpad"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by niranjan_rao on 2011-06-13
Documentation/numerous web sites seems to be suggesting that this is possible. However not sure how to achieve this. I already have scroll based on two fingers. It's other gestures like pinching, three finger swipe that I am interested in.

xinput list-props for trackpad seems to indicate that synaptics driver is detecting trackpad as multitouch pad. This is on Fujitsu/AH530 notebook with ubuntu 11.04 installed.


Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (127):	1
	Coordinate Transformation Matrix (129):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (244):	1
	Device Accel Constant Deceleration (245):	2.500000
	Device Accel Adaptive Deceleration (246):	1.000000
	Device Accel Velocity Scaling (247):	12.500000
	Synaptics Edges (248):	1781, 5579, 1660, 4760
	Synaptics Finger (249):	24, 29, 255
	Synaptics Tap Time (250):	180
	Synaptics Tap Move (251):	250
	Synaptics Tap Durations (252):	180, 180, 100
	Synaptics Tap FastTap (253):	0
	Synaptics Middle Button Timeout (254):	75
	Synaptics Two-Finger Pressure (255):	280
	Synaptics Two-Finger Width (256):	6
	Synaptics Scrolling Distance (257):	113, 113
	Synaptics Edge Scrolling (258):	0, 0, 0
	Synaptics Two-Finger Scrolling (259):	1, 0
	Synaptics Move Speed (260):	1.000000, 1.750000, 0.035094, 40.000000
	Synaptics Edge Motion Pressure (261):	29, 159
	Synaptics Edge Motion Speed (262):	1, 455
	Synaptics Edge Motion Always (263):	0
	Synaptics Off (264):	1
	Synaptics Locked Drags (265):	0
	Synaptics Locked Drags Timeout (266):	5000
	Synaptics Tap Action (267):	2, 3, 0, 0, 1, 3, 2
	Synaptics Click Action (268):	1, 3, 2
	Synaptics Circular Scrolling (269):	0
	Synaptics Circular Scrolling Distance (270):	0.100000
	Synaptics Circular Scrolling Trigger (271):	0
	Synaptics Circular Pad (272):	0
	Synaptics Palm Detection (273):	0
	Synaptics Palm Dimensions (274):	9, 199
	Synaptics Coasting Speed (275):	20.000000, 50.000000
	Synaptics Pressure Motion (276):	29, 159
	Synaptics Pressure Motion Factor (277):	1.000000, 1.000000
	Synaptics Grab Event Device (278):	1
	Synaptics Gestures (279):	1
	Synaptics Capabilities (280):	1, 0, 1, 1, 1, 1, 1
	Synaptics Pad Resolution (281):	143, 88
	Synaptics Area (282):	0, 0, 0, 0
	Synaptics Jumpy Cursor Threshold (283):	0

---

