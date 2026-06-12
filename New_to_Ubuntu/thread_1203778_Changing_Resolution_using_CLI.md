---
title: "Changing Resolution using CLI"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by ncc1701e on 2009-07-03
Does anyone know how I can change screen resolution from 1920x1200 using the command line? I know I"d have to pass a command to the nvidia X configuration util.

I'm looking for the command equivalent of:

change resolution to 1280x1024

Normally one would do this using GUI but I need to include this command in to a shell script Im putting together.

thanks

---

### Post by K.Y.A on 2009-07-03
You can find commands using this command:

```
man -k "resolution"
```


But to change your screen resolution, you use the xrandr command.

First, run xrandr

```
xrandr
```

This will give you a long list of available resolutions for your monitor. My output:
```
Screen 0: minimum 320 x 175, current 1280 x 1024, maximum 1440 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1440x900       50.0  
   1360x768       51.0     52.0  
   1152x864       53.0     54.0     55.0     56.0  
   1024x768       57.0     58.0     59.0     60.0     61.0     66.0  
   960x540        62.0  
   840x525        63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0  
   720x450        71.0  
   720x400        72.0  
   700x525        73.0  
   680x384        74.0     75.0  
   640x480        76.0     77.0     78.0     79.0  
   640x400        80.0  
   640x350        81.0  
   512x384        82.0     83.0     84.0  
   400x300        85.0  
   320x240        86.0     87.0  
   320x175        88.0  
   1280x1024      89.0* 
```

The one with the ** by it is your current resolution. Mine is currently 1280X1024.

**To make it 1280X1024, use this command:**
```

xrandr -s 1280X1024
```

---

