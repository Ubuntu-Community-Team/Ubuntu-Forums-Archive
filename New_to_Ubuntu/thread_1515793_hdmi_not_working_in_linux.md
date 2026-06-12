---
title: "hdmi not working in linux"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by fernando.vs on 2010-06-22
hi, 

i have a new laptop asus ul30vt-a1, everything is working fine, however the hdmi interface is not working at all, i have already tested it in windows 7 and its ok, however in ubuntu 10.4 or fedora 13 is not. 

this is the output of the xrandr command in my laptop: 

 Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 293mm x 164mm
   1366x768       60.0*+
   1360x768       59.8  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DP1 disconnected (normal left inverted right x axis y axis)

as it shows, the hdmi interface is not showed at all. the vga interface works fine. 

i havent installed the propietary driver of the nvidia gpu yet. 

thanks all for your help.

---

### Post by LowSky on 2010-06-24
install the nvidia driver

---

