---
title: "wacompcl not detecting tablet"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by patchido on 2010-04-13
well, i have a wacom tablet, model intous 3, and i hadnt got the time of using it since a long time, and now that i have some time i tried using it in Karmic but when i use wacomcpl nothing apperas on the program, just it says select device, and a scroll but nothing in it, any suggestions? it does work, i mean the tablet, but in gimp the pressure wont work and the eraser is taken as if it was the same as the point, i suppose the same thing will fix both problems

---

### Post by Favux on 2010-04-13
Hi patchido,

You probably need a modified  wacom .fdi.  See [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") on the Wacom tablets thread for explanation and .fdi.

---

### Post by patchido on 2010-04-13
ok, that did work, now wacomcpl displays my stulus and eraser, is that all it should display?, but gimp doesnt recognize my sensitivity still, any sugestions?

---

### Post by Favux on 2010-04-13
Hi patchido,

Good!
> now wacomcpl displays my stulus and eraser, is that all it should display?
Depends on what you have.  Do you have the Wacom mouse or a pad (buttons on the tablet)?

For Gimp you need to configure the extended input devices.  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

---

### Post by patchido on 2010-04-14
its a pad

---

### Post by Favux on 2010-04-14
OK, which .fdi are you using?  If it's the new-generic then the filter on the wacom names section is getting your pad.  You can either try the first .fdi, test2, or we can fix the filter.  For that I need to see your lshal:
```
lshal>patchido_lshal.txt
```
You can right click on it and compress it with Create Archive and then post it using Managing Attachments.

---

### Post by patchido on 2010-04-14
i used the new generic, i did what said the last part of the wiki, worked great, pressure is now showing on gimp, only remining problem is that the eraser is still as if it was the pen :S

---

### Post by Favux on 2010-04-14
You need to point to the little eraser icon with the eraser and then Save that assignment.

---

### Post by patchido on 2010-04-14
perfect! now for my last question, how do i program the side buttons? it is an intous 3 it has 3 buttons and a slider in each side of the tablet

---

### Post by Favux on 2010-04-14
Good!  So now you see the pad?  If you go back to post #176 you'll see it links you to Shatterblasts post on the next page where he shows you how.

---

### Post by patchido on 2010-04-14
ok, i think i have the idea of how to do it, but how do i know which button is which? i have this tablet [http://graphicssoft.about.com/library/graphics/Intuos3-6x8.jpg]("http://graphicssoft.about.com/library/graphics/Intuos3-6x8.jpg") it has two sides with buttons.

---

### Post by Favux on 2010-04-14
Hi patchido,

This link will show you the button layout:  [http://kaeru.my/articles/technical/setting-up-and-using-intuos-tablet-on-linux/ubuntu-setup](http://kaeru.my/articles/technical/setting-up-and-using-intuos-tablet-on-linux/ubuntu-setup)

---

### Post by patchido on 2010-04-14
well, im doing something wrong while stablishing the keystrokes have a look at this

```
pato@pato-laptop:~$ xsetwacom set pad striprup "core key +"
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'pad'
pato@pato-laptop:~$ 

```

---

### Post by patchido on 2010-04-14
also, pad isnt recognized as a device :S

pato@pato-laptop:~$ xsetwacom list
eraser           eraser    
stylus           stylus

[code]pato@pato-laptop:~$ xinput --list

"stylus cursor"	id=16	[XExtensionKeyboard]
	Type is Wacom Cursor
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 40640
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 30480
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
	Axis 4 :
		Min_value is -1023
		Max_value is 1023
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"stylus pad"	id=17	[XExtensionKeyboard]
	Type is Wacom Pad
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 8
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 40640
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 30480
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is 0
		Max_value is 4096
		Resolution is 1
	Axis 4 :
		Min_value is 0
		Max_value is 4096
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"stylus"	id=18	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 40640
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 30480
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
pato@pato-laptop:~$ 
[code]

---

### Post by Favux on 2010-04-14
Hi patchido,

From the xinput output it looks like you have the Wacom tablet mouse along with the pad.  Is that right?  If you are using the new-generic .fdi I need you lshal output as described in an earlier post above.

---

### Post by patchido on 2010-04-14
here it is :D

---

### Post by Favux on 2010-04-14
That's weird, there's no Wacom sections in the lshal.  Did you have your Intous3 plugged in?   It it usb right?  In a terminal enter:
```
lsmod | grep wacom
```
to see if the wacom usb kernel driver is loading.

---

### Post by patchido on 2010-04-14
im sorry, i didnt know i had to have it plugged, this is the updated file

---

### Post by Favux on 2010-04-14
Ok, here's the problem.  For some reason the Intuos3 is different and the pad is subdev_1 and the cursor (Wacom mouse) is subdev_0.  So the contains_not filter in the Wacom names "parser" is screening them out.  So change that section of the .fdi from:
```
  <!-- Wacom names "parser" -->
  <device>
    <match key="info.udi" contains_not="subdev_0">
    <match key="info.udi" contains_not="subdev_1">
    <match key="info.udi" contains_not="subdev_2">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="info.product" type="string">stylus</merge>
      </match>
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="info.product" type="string">eraser</merge>
      </match>
      <match key="input.x11_options.Type" contains="cursor">
        <merge key="info.product" type="string">cursor</merge>
      </match>
      <match key="input.x11_options.Type" contains="pad">
        <merge key="info.product" type="string">pad</merge>
      </match>
      <match key="input.x11_options.Type" contains="touch">
        <merge key="info.product" type="string">touch</merge>
      </match>
    </match>
    </match>
    </match>
  </device>
```
to
```
  <!-- Wacom names "parser" -->
  <device>
    <match key="info.udi" contains_not="subdev_2">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="info.product" type="string">stylus</merge>
      </match>
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="info.product" type="string">eraser</merge>
      </match>
      <match key="input.x11_options.Type" contains="cursor">
        <merge key="info.product" type="string">cursor</merge>
      </match>
      <match key="input.x11_options.Type" contains="pad">
        <merge key="info.product" type="string">pad</merge>
      </match>
      <match key="input.x11_options.Type" contains="touch">
        <merge key="info.product" type="string">touch</merge>
      </match>
    </match>
  </device>
```
Reboot and pad and cursor should now show up in 'xinput --list' and 'xsetwacom list'.

---

### Post by patchido on 2010-04-14
, now i can get to the drawing, you really know what you are going, gratz

---

### Post by patchido on 2010-04-14
actually, one more thing, when i restarted it the keys that i had already given xsetwacom restarted to default, will i have to run the commands every time i restart the computer?

---

### Post by Favux on 2010-04-14
Great!  We got it working for you.

Sure, you need to set wacomcpl's .xinitrc to autostart.  See "Section 3:   Calibrating your Tablet or Tablet PC." at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by patchido on 2010-04-14
i see, this thing is actually very good supported :) did you do this? i mean the development on it? is tilt supported? do you know how i could test it?

---

### Post by Favux on 2010-04-14
Yes Wacom is very well supported in linux thanks to the LWP (linux wacom project) and former head developer Ping Cheng.  See:
[http://linuxwacom.sourceforge.net/index.php/main](http://linuxwacom.sourceforge.net/index.php/main)
[http://sourceforge.net/projects/linuxwacom/](http://sourceforge.net/projects/linuxwacom/)

---

### Post by patchido on 2010-04-14
i found [this]("http://alexmac.cc/tablet-apps/") very usefull, it actually gave me a very good idea on a project that i want to develop, i want to make a robot that is controlled via the stylus pen of the tablet, but for it i need to know how does the information of tilt and pressure get into the computer, i dont know if you could help me with that.

---

### Post by Favux on 2010-04-14
If you use the two links I gave you, you'll find a lot of information including source code and a link for developers.  
Good luck!

---

### Post by patchido on 2010-04-14
the sites are kind of weird, i did find the sample code, but i dont really understand what is happening, what language is it written in? sorry if the question might be noobish, i kind of am :) i know java, and thats about it, but the language itself is not what matters, i do know how to program, so my pen is read by 0x823 but the tilt and pressure? im not sure how all this thing work, i believe i have to go first into the bases, cause i dont really even know what that number mean, could you give me a hint where to look at to learn? 

you have really been of great help, thx alot

---

### Post by Favux on 2010-04-14
You are welcome.  It's been fun.

It's written in C which I am just beginning to learn.  I know a little Python.  You're just going to have to look some more.  The development traffic link is where the developers post and I know the talked about a tilt patch in the last few months.  You can post for help by joining the genereal discussion link (linuxwacom-discuss).  You'll also want to download the source code and look at the various files.

---

