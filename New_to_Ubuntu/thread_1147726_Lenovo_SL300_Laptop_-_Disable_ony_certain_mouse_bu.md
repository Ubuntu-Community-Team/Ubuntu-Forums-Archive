---
title: "Lenovo SL300 Laptop - Disable ony certain mouse buttons"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by dorseye on 2009-05-03
I have a Lenovo SL300 laptop running Ubuntu 9.04

I want to disable the Alps touchpad at the bottom of the computer, and its buttons, but leave the "eraser" style mouse in the middle of the keyboard working, and I want to leave its mouse buttons directly below the keyboard working as well. 

I install gsynaptics and turned off touchpad, but this unfortunately ALSO turns off the "eraser" mouses' buttons too. In windows I can turn off just one of the mouse/buttons and leave the other mouse/buttons on. 

Any ideas? My xinput is below, but I don't know if that helps at all?


```
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Logitech USB Receiver"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
"Lenovo ThinkPad SL Series extra buttons"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"DualPoint Stick"	id=7	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"AlpsPS/2 ALPS DualPoint TouchPad"	id=8	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is 767
		Resolution is 1
"Logitech USB Receiver"	id=9	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

---

