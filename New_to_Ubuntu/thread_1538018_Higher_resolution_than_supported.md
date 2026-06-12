---
title: "Higher resolution than supported?"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by OptimalApple on 2010-07-24
Hello Forums!

Today I got a new monitor to accompany my laptop, and to use for console gaming. The resolution that it runs at (1920 x 1080), however does not show up as an option in my display settings. My graphics card drivers are installed and working but the highest option I get is 1280 x 800. Is there anyway to run both my laptop's built in monitor and my new one at their best resolutions? (1280 x 800 and 1920 x 1080). Any help or insight is much appreciated :D

---

### Post by davidmohammed on 2010-07-24
difficult to say without knowing what your graphics card is....

in a terminal type

lspci | grep VGA

also

copy and paste the contents of the file (if it exists) here

/etc/X11/xorg.conf

finally in a terminal run

xrandr

and copy and paste the contents here.

---

### Post by OptimalApple on 2010-07-24
My card is a ATI Radeon HD 3200

cody@cody-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2560 x 800
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1280x768       60.0 +
   1280x720       60.0 +
   1024x768       60.0 +
   1280x600       60.0 +
   1024x600       60.0 +
   800x600        60.0 +
   800x480        60.0 +
   720x480        60.0 +
   640x480        60.0 +
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       75.0     60.0* 
   1280x768       59.9  
   1280x720       60.0  
   1024x768       75.0     60.0  
   1280x600       60.0  
   1024x600       60.0  
   800x600        75.0     60.3     56.2  
   800x480        60.0  
   720x480        60.0  
   640x480        75.0     60.0

---

### Post by davidmohammed on 2010-07-25
are you using the default ATI graphics driver or the proprietary driver (catalyst) from the ATI website?

I suspect, you should try and [install]("http://blip.tv/file/2639239") the proprietary driver to see if the resolution can be increased.

---

