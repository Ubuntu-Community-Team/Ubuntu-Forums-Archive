---
title: "how do i load the default mouse driver?"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by expxe on 2009-12-03
i want my mouse to be just like it was after a fresh install. thanks!

---

### Post by Daveth on 2009-12-03
what is it doing now that it was not before then? A bit more detail would help here.

---

### Post by expxe on 2009-12-03
> **Daveth said:**
> what is it doing now that it was not before then? A bit more detail would help here.

i just want my scroll wheel to be back to the way it way after a fresh install, so how do i set it back?

---

### Post by expxe on 2009-12-04
anyone? this should be an easy request to fill right?

---

### Post by Terl on 2009-12-04
What is it doing now tht it was not doing?  Saying "the way it was before" is not clear enough.  Have you changed anything?

---

### Post by expxe on 2009-12-04
the middle click doesn't work the way it used to, before it would open/close tabs in firefox, now it switches between click-scroll & smooth scroll (for those who have the logitech mx rev), because i reset the mouse. i just want the default mouse driver, without having to reinstall the whole OS.

---

### Post by mike555 on 2009-12-04
I don't think it's the driver if it only misbehaves in Firefox , check the Firefox settings ( edit>preferences>advanced )

---

### Post by expxe on 2009-12-04
no, it misbehaves everywhere, i was just using firefox as an example. 

so how do i reset the mouse driver? or is it impossible? 

only a reset will fix my mouse, i am serious. i am willing to go as far as a reinstall. i want my mouse to work properly. but before i do that i was thinking this is linux, there must be a better way, even in windows you don't have to resinstall the OS to fix a mouse (but then there are actually drivers from the manufactures for it hehe)

---

### Post by Terl on 2009-12-04
Did you change something in configurations before this happened?  I doubt you have to reinstall a driver or the O/S.  Usually these things happen becuase a minor tweak or change was done somewhere.  Have you checked under the system menu - there is a mouse configuration tool there...

---

### Post by expxe on 2009-12-04
no, i reset the mouse (by left click, on/off switch, 5x right click method). do you know what i mean? i take it you have the same mouse, not exactly supported right out of the box (for ubuntu)

look, is there even a default driver? why aren't you answering my question? 

i feel that i have posted in the wrong section, thought this should easily be a beginner's problem but if it is an advanced problem in linux i can ask a mod to move the topic so that more experienced users can have a look. 

i will ask one more time, how do i load the default mouse driver? i want my mouse to be just like it was after a fresh install. 

thanks

---

### Post by Terl on 2009-12-04
Sorry, I do not have that mouse, I just use a regular mouse.  If you have something programmable that you reset, I can't help.    

And, yes, there is a mouse driver and it is loaded...your mouse works, just not the way you wanted because you changed its programming by resetting it.  Sorry, I thought it was just a regular wheel mouse.  Not sure how to reprogram the mouse.  Have you tried googling the mouse model with a + linux after it?  Sometimes that returns a wealth of info.

---

### Post by jtuchscherer on 2009-12-04
I guess people would be able to help you better, if you would be more detailed about what you did to make the mouse misbehave. Did you install a custom driver for your mouse? Did you compile a kernel with that driver? Or did you just change a setting somewhere in the configuration window?

The default mouse driver comes with the xserver. You probably could just reconfigure your xserver to get the default mouse settings back.
Could you post the output of the following command (it will list all your input devices like keyboard and mouse):

```
xinput list
```

---

### Post by expxe on 2009-12-04
```
xinput list
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
"Logitech Logitech USB Keyboard"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 14
"Logitech Logitech USB Keyboard"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Logitech USB Receiver"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
"Power Button"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=7	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
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
"Logitech USB Receiver"	id=8	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 24
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

### Post by mjwilson1313 on 2009-12-04
why are you doing this... in every thread you open its a dig at ubuntu.. your tag is always being sarcastac .... do you want help or just to see what type of hell you can raise on the forums?

---

### Post by jtuchscherer on 2009-12-05
Can you answer this as well?

> **jtuchscherer said:**
> Did you install a custom driver for your mouse? Did you compile a kernel with that driver? Or did you just change a setting somewhere in the configuration window?


Your output from the xinput command looks normal to me. I would assume that you are still using the default driver and you just changed a configuration setting.

---

### Post by expxe on 2009-12-05
yes, so how can i change it back to default? as if i just plugged in my mouse for the first time

---

### Post by expxe on 2009-12-05
comon ppl, is it THAT hard?

---

### Post by jtuchscherer on 2009-12-05
Did you install a custom driver for your mouse? Did you compile a kernel with that driver? Or did you just change a setting somewhere in the configuration window?

---

### Post by expxe on 2009-12-05
> **jtuchscherer said:**
> Did you install a custom driver for your mouse? Did you compile a kernel with that driver? Or did you just change a setting somewhere in the configuration window?

no special/custom/kernal drivers or changed settings, i reset the mouse (by left click, on/off switch, 5x right click method), then the scroll button doesn't work properly amymore.

I just want the default settings, just like it was after a fresh install.

---

### Post by jtuchscherer on 2009-12-05
Have a look at this:
[http://www.toosweettobesour.com/2009/05/13/logitech-mx-revolution-revoco-in-ubuntu-904-jaunty-click-to-click-even-after-a-resumewakeup/](http://www.toosweettobesour.com/2009/05/13/logitech-mx-revolution-revoco-in-ubuntu-904-jaunty-click-to-click-even-after-a-resumewakeup/)

That was the first thing that google brought up. I cannot try it out since I don't have your mouse. But if you have a look at a few other links that google shows I am sure you will figure it out. You are not the only one with this problem

---

### Post by jtuchscherer on 2009-12-05
Have a look at this:
[http://www.toosweettobesour.com/2009/05/13/logitech-mx-revolution-revoco-in-ubuntu-904-jaunty-click-to-click-even-after-a-resumewakeup/](http://www.toosweettobesour.com/2009/05/13/logitech-mx-revolution-revoco-in-ubuntu-904-jaunty-click-to-click-even-after-a-resumewakeup/)

That was the first thing that google brought up. I cannot try it out since I don't have your mouse. But if you have a look at a few other links that google shows I am sure you will figure it out. You are not the only one with this problem

---

### Post by expxe on 2009-12-06
i skimmed thru the info in your link and it looks exactly what i want to do, however i just ran update manager this morning and the problem was fixed (it was a kernel update). so i don't have to do anything now

---

### Post by expxe on 2009-12-06
thanks for taking the time to help out, hopefully my mouse won't change, but if it does i'll know the first thing i'm gonna try to fix it

---

