---
title: "Hp tx1000 Tablet configuring touch"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by izbm on 2011-07-20
Hey can anyone help me configure my hp tx1000's tablet?
It is somewhat inaccurate with landscape and very inaccurate in portrait. Any tips advice or help for making it more accurate? 
Im running pinguy 11

---

### Post by skatinjj on 2011-07-20
Is there an app or setting somewhere that will allow you to calibrate the tablet?

---

### Post by Favux on 2011-07-20
It could depend on what X driver is running the touchscreen.  Enter in a terminal *xinput list* and in the output you'll see your touch screen "device name".  Then take that and run this command:
```
xinput list-props "device name"
```
That should show us what driver is in use.  Go ahead and post both outputs.

---

### Post by izbm on 2011-07-21
I got a list of devices like this which one should i select?

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eGalax INC. USB TouchController         	id=11	[slave  pointer  (2)]
&#9116;   &#8627; eGalax INC. USB TouchController         	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=15	[slave  keyboard (3)

---

### Post by Favux on 2011-07-21
It's these:
```
&#9116; &#8627; eGalax INC. USB TouchController id=11 [slave pointer (2)]
&#9116; &#8627; eGalax INC. USB TouchController id=12 [slave pointer (2)]
```
Since there are two and they have the same name use the id # to distinguish them as in:
```
xinput list-props 11
```
instead of:
```
xinput list-props "eGalax INC. USB TouchController"
```

---

### Post by izbm on 2011-07-21
Kk here it is


$ xinput list-props 11
Device 'eGalax INC. USB TouchController':
	Device Enabled (149):	1
	Coordinate Transformation Matrix (151):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (269):	0
	Device Accel Constant Deceleration (270):	1.000000
	Device Accel Adaptive Deceleration (271):	1.000000
	Device Accel Velocity Scaling (272):	10.000000
	Evdev Axis Inversion (273):	0, 0
	Evdev Axis Calibration (274):	<no items>
	Evdev Axes Swap (275):	0
	Axis Labels (276):	"Abs X" (267), "Abs Y" (268)
	Button Labels (277):	"Button Left" (152), "Button Unknown" (266), "Button Right" (154), "Button Wheel Up" (155), "Button Wheel Down" (156)
	Evdev Middle Button Emulation (278):	0
	Evdev Middle Button Timeout (279):	50
	Evdev Wheel Emulation (280):	0
	Evdev Wheel Emulation Axes (281):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (282):	10
	Evdev Wheel Emulation Timeout (283):	200
	Evdev Wheel Emulation Button (284):	4
	Evdev Drag Lock Buttons (285):	0
izbm@izbm-HP-Pavilion-tx1000-Notebook-PC:~$

---

### Post by Favux on 2011-07-21
Alright your touchscreen is on the evdev X driver rather than the eGalax touchscreen X driver.  I don't know if that is how it is suppose to be.  Maybe eGalax stopped updating their driver for the newer releases?  I think at one point you could use the evtouch driver and I think that got folded into evdev.

Rotation with evdev got broken in Natty because there was a bug with the axes swap method and so you had to use the Coordinate Transformation Matrix (CTM) to rotate.  But there is a fix now so I guess it doesn't matter which way pinguy is doing it.

Notice that you have no coordinates:
```
Evdev Axis Calibration (274): <no items>
```
So that is likely the problem.  Check if pinguy has a calibration program in its repositories.  The other older drivers had calibration programs.  If you don't find one you can use [xinput_calibrator]("http://www.freedesktop.org/wiki/Software/xinput_calibrator") to calibrate a tablet on evdev.  I don't think there is a deb or PPA for you so if it isn't in your repositories you'll have to compile it:  [https://github.com/tias/xinput_calibrator](https://github.com/tias/xinput_calibrator)

---

