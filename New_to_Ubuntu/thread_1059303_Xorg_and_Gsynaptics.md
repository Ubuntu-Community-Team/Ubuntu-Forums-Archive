---
title: "Xorg and Gsynaptics"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by WastePotato on 2009-02-03
Hi,


 I'm trying to change some options on my touchpad and get this error when starting gsynaptics.

[http://img23.imageshack.us/img23/3606/screenshotac0.png](http://img23.imageshack.us/img23/3606/screenshotac0.png) 

The question is, which options do I enter in Xorg.conf?  



Thanks.

---

### Post by binbash on 2009-02-03
[http://ubuntuforums.org/showthread.php?t=271052&highlight=touchpad](http://ubuntuforums.org/showthread.php?t=271052&highlight=touchpad)

start reading at the end.

---

### Post by WastePotato on 2009-02-03
Cheers mate. Thanks. :)

---

### Post by LinuxPS2 on 2009-02-03
I thought as of 8.10 you would have to add it as a HAL fdi... atleast according to
[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig")

However, I don't know about anyone else but that simply didn't work for me.

Also, when I run 'xinput list' my touchpad doesn't even show up, I get this:
```
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Macintosh mouse button emulation"	id=2	[XExtensionPointer]
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
"ImPS/2 Logitech Wheel Mouse"	id=3	[XExtensionPointer]
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
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

```

Any thoughts?...

---

