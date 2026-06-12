---
title: "Force Native Resolution for External Montior"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by altonbr on 2010-01-24
I have a standard-resolution 19" monitor that I've been using for years as my main monitor.

Now that I sold my computer and am using a netbook, I need my 19" monitor to display at 1280x1024, but xrandr can only find 1360x768 as my maximum resolution.
```
$ xrandr
Screen 0: minimum 320 x 200, current 2176 x 864, maximum 4096 x 4096
VGA1 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS1 connected 1024x600+1152+264 (normal left inverted right x axis y axis) 195mm x 113mm
   1024x600       60.0*+   40.0  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1
```

How do I force 1280x1024 using Ubuntu 9.10?

---

