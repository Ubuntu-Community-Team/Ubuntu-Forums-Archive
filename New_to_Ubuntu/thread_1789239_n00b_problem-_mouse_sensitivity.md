---
title: "n00b problem- mouse sensitivity"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by Winelord on 2011-06-23
Hi all. Just did full install of Lubuntu 11.04 on an old laptop (Fujitsu Siemens Amilo) via CD burned from iso.

The mouse movement is erratic & I can't adjust it. &
I've used 2 wired optical mice, with the same results. 
I've tried via the GUI & terminal, but my changes don't take effect. The trackpad on the laptop works fine.

In the GUI (Preferences>Keyboard & Mouse), the window closes immediately after I release the left button, so my changes aren't saved. Same with trying adjustments via the trackpad.

I've tried using "xinput" via the terminal, but I'm struggling.
In the GUI, the mouse Acceleration is 20, Sensitivity is 100.
In xinput, the values for the mouse & trackpad are identical:
> PtrFeedbackClass id=0
accelNum is 20
accelDenom is 10
threshold is 10

That doesn't make sense to me, I thought threshold=sensitivity, so I assumed that the mouse would show a higher threshold than the trackpad?

I've tried manually changing the mouse variables via "set-ptr-feedback" but this doesn't affect the mouse behaviour.

I've only been using Ubuntu for a week (mainly on another laptop with no issues) and I'm stuck now. My two mice work fine on the other laptop (Ubuntu 11.04).
Any help will be gratefully received!

---

### Post by Winelord on 2011-06-24
I've got the following info through xinput list --long:

>    &#8627; Microsoft  Compact Optical Mouse 500    	id=10	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 10
		Buttons supported: 7
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right
		Button state:
		Class originated from: 10
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 10
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative

&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 12
		Buttons supported: 12
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right None None None None None
		Button state:
		Class originated from: 12
		Detail for Valuator 0:
		  Label: Rel X
		  Range: 1472.000000 - 5472.000000
		  Resolution: 85000 units/m
		  Mode: relative
		Class originated from: 12
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: 1408.000000 - 4448.000000
		  Resolution: 94000 units/m
		  Mode: relative


Presumably I need to make the mouse values identical to the trackpads?
How do I do that?

---

