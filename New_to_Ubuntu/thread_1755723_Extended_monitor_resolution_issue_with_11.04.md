---
title: "Extended monitor resolution issue with 11.04"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by _dk_ on 2011-05-11
Hi,

I just installed a fresh copy of Ubuntu 11.04 and installed a new acer monitor i got as an extended monitor. However, when i set both my laptop and external monitor to their optimum resolutions, the last inch or so of my extended monitor goes black as if the desktop does not extend to that area. The odd thing is that i can move my mouse cursor to that area and it shows up fine. Even the top toolbar extends to that area but when it comes to the desktop itself, any program windows, menus etc.. will get cut off from that point on. I have attached a screenshot of my desktop. Does anyone know whats happening here? Also, here is my output when i run xrandr -q :

Screen 0: minimum 320 x 200, current 2960 x 1050, maximum 8192 x 8192
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+   50.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1680x1050+1280+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+
   1600x1200      60.0  
   1400x1050      60.0  
   1280x1024      75.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DVI1 disconnected (normal left inverted right x axis y axis)

---

### Post by _dk_ on 2011-05-11
Sorry. here is the screenshot.

---

### Post by Ni-el on 2011-05-27
No, but I want to know about this too (same problem on  4 Series Intel Graphics Controller).
So far, the only difference I see is the xserver-xorg-video-intel drver. 10.10 Maverick used version 2.12 and 11.04 is using version 2.14. Coincidentally, Fedora 15 (newest) has the same problem and they use the 2.14 version. I am back to 10.10 right now but when I find the energy to try this again, I will try to install 11.04 and downgrade to the old driver. I'll let you know how it turns out if someone doesn't try it first.

---

