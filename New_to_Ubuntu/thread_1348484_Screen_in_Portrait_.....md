---
title: "Screen in Portrait ...."
date: 2009-12-07
forum: New to Ubuntu
---

### Post by expatCM on 2009-12-07
I just set up a home theatre again.  This time with Ubuntu 9.10.  The setup is fine with the flat panel I used but when I connect it to a projector the output only occupies say half of the projection screen and it appears in portrait format.

Since this used to work before I reinstalled I know it has to be a setting but I do not know which.

I am using a nVidia video card and the resolution is 1024 x 768.  I have been through the nVidia X Server Settings gui, much of what is there does not make too much sense to me but I cannot see any obvious setting to change.

Everything else is working ....  it is just the wrong orientation.

Any ideas?

---

### Post by rubenverweij on 2009-12-07
Maybe you could try to rotate it with xrandr. Don't know whether this works for a second screen too, though.

---

### Post by expatCM on 2009-12-07
It is only the one screen.  All I did was change physical location and use the projector instead of the flat panel display.

Do you happen to know if xrandr is only command line and what should be changed?

---

### Post by expatCM on 2009-12-08
I may have accidentally discovered a simple fix.

I opened xorg.conf and at the end of the Section "Device" I added the following line - 

Option "RandRRotation" "true"

When I restarted a new line had appeared in nVidia X Server Settings which allows rotating the output ..... and that (subject to testing) is what I need....

---

### Post by rubenverweij on 2009-12-08
Glad you solved it. Should you need to work with xrandr, here is a mini how-to: :D
Firstly, find out how your screen is called:
```
xrandr
```
This should output your screen name. In my case it displays:
```
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+
   640x480        59.9  

```
So, the name is LVDS1.
Then, to rotate the screen, type:
```
xrandr --output LVDS1 --rotate [normal,inverted,left,right]
```
Good luck!

---

### Post by expatCM on 2009-12-09
Thank you for posting the extra information ...  it is really good to have a broader picture to hand ....

---

