---
title: "Right click on ubuntu installed on a Mac laptop"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by newbuntuxx on 2009-05-16
Hey

I just installed Ubuntu 9.04 on my Mac laptop (it has an intel chip). Everything worked right out of the box, wireless, sound, function keys etc....

but, given that Mac laptops only have one button to use for click (left click only) i want to add the right click as well, as that can be useful from time to time :)..

when i used OS 10, I would basically place two fingers on the tracking pad, and then click, that would give me a right click. 

Is it possible to do the same on ubuntu. 

This is what i know so far:

/etc/default/mouseemu is the file that i should edit, the question is: how can i add that functionality to the file, that is, both fingers on the tracking with a click equal a right click?

your help is appreciated!

---

### Post by radiocognition on 2009-05-16
The defaults on my macbook pro have "three finger click" as right click.  I just started using this - for me it's not a deal breaker.  Please post your solution if you ever figure it out

---

### Post by ugm6hr on 2009-05-16
Check out
```
man synaptics
```

The bit you want is:
```
       Option "TapButton2" "*integer*"
```

Where *integer* is **2** (I think) for right mouse button.

Since xorg settings no longer directly control synaptics, you might need to read the relevant links here:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I'm looking at this (to enable SHMConfig to allow syndaemon to disable tapping when typing) myself, so might be able to post back with more relevant detail later.

EDIT: 
Link: [https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL](https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL)

Maybe something like the following in /etc/hal/fdi/policy/synaptics.fdi
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.TapButton2" type="string">2</merge>
  </match>
 </device>
</deviceinfo>
```

And then reboot.  And keep finders crossed!  Good luck with it.

---

### Post by newbuntuxx on 2009-05-19
found this excellent wiki:

[https://help.ubuntu.com/community/MacBook4-1/Jaunty](https://help.ubuntu.com/community/MacBook4-1/Jaunty)


thanks for the help

---

