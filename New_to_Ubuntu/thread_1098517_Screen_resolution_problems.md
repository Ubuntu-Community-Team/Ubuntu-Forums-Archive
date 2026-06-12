---
title: "Screen resolution problems"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-03-17
I have a 19" screen attached to my lap top. I had it set up the way I like it...but I had to do a presentation today with a projector which was causing a problem and so I must have screwed up the settings of the screen display. When I go "~$ xrandr -q", i get the following....I had much more resolutions than these ...I now cannot set my 19" screen to the higher resolution that it was on...what can I do?

Thanks.


~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 768
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1024x768       75.0     60.0* 
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected (normal left inverted right x axis y axis)
   1024x768       60.0 +   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)


~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090317224114

but no way to increase the resolutions etc.

---

### Post by Bodsda on 2009-03-17
dpkg-reconfigure -phigh xserver-xorg no longer does what you think it does, it doesnt seem to touch the graphics, try booting to recovery mode from grub and selecting the xfix option

---

