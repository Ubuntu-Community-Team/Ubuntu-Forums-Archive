---
title: "Can't run external monitor/HDTV"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by sirthomas711 on 2010-05-28
I'm running a Dell Inspiron E1505 with an ATI Mobile Radeon X1400 video card.  I connect my Sony Bravia HDTV with a VGA cable, and Windows would run it, but with Ubuntu, it will recognize when it's plugged in, so far as to even say that it's a Sony TV and determine the available screen resolutions, but it will not send a signal to the TV.  I just installed two days ago, and so far this is the only problem I'm having with it.  Any ideas?

---

### Post by tom.swartz07 on 2010-05-28
did you, by chance 'enable' the screen?

you would click on the monitor, and select 'on' then say mirror desktop. 

should work after that; I do the same with a radeon x1270 card and a samsung tv

---

### Post by sirthomas711 on 2010-05-28
Yeah, I did.  Like I said, it connects to it, and it will tell me it's active, but I'm getting no signal to the TV.  Not sure what to do.

---

### Post by tom.swartz07 on 2010-05-28
is there a dedicated 'function' key for the monitors? sometimes its controlled by the hardware, rather than software. 

also, post the output of ```
xrandr
``` when you have the VGA cable plugged in and not plugged in

---

### Post by sirthomas711 on 2010-05-28
I'll try that.  And now that I think about it I believe there is a function button for that.  I'm at work right now and will be for another 2 1/2 hours.  Can I add you to my friends/PM later after I've had a chance to run that command?

---

### Post by tom.swartz07 on 2010-05-28
> **sirthomas711 said:**
> I'll try that.  And now that I think about it I believe there is a function button for that.  I'm at work right now and will be for another 2 1/2 hours.  Can I add you to my friends/PM later after I've had a chance to run that command?

sure thing, buddy.
Ill be off and on here regularly for the rest of the day.

How about you post the output and such here? that way it could be available to more than just you and I. More heads are better than none! :P

---

### Post by sirthomas711 on 2010-05-28
True.  I'll do that.  I get off around 5 EST so I'll post it then.  Thanks for the help.

---

### Post by sirthomas711 on 2010-05-28
Without it plugged in:

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       61.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)


With it plugged in:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080      60.0 +
   1280x1024      60.0  
   1360x768       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        60.0  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       61.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9* 
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)


Now it's doing something new also.  When I enable it I can set the resolution(although still no signal) but then after a few seconds(after I close the menu for the monitors) it changes to 1024x768(my laptop runs 1280x800) and when I open the menu back up it's changed to mirror screens and the resolution being at 1024x768.  I'm noticing that in the terminal it's saying 1024x768 as both resolutions, but the menu(at that point was reading 1280x800 and 1920x1080 respectively.

---

