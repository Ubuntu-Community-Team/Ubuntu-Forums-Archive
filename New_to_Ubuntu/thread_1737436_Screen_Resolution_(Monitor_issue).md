---
title: "Screen Resolution (Monitor issue)"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by GenghisMcB on 2011-04-23
I've just installed Ubuntu 10.10 x 64 on my desktop, and it's not  offering the correct screen resolution for my monitor.  I've downloaded  and installed the proprietary nvidia drivers for my graphics card (a  GeForce GTS 250), which helped slightly, but the resolutions on offer  only go up to 1360x768, which makes me suspect my monitor isn't being  recognised properly.  My monitor is a Medion MD30422PV and native  resolution is 1680x1050 at 59Hz.  I have almost no experience using the  terminal / command line, so if anyone could walk me through the solution  to this problem I'd be very grateful.

---

### Post by grahammechanical on 2011-04-23
When you installed the nvidia drivers did not you also get a NVIDIA X-Server Settings utility? It should be in the Administration menu. On my system this utility tells me that I am using the 270.41.06 driver to run my Samsung Syncmaster TD200HD at 1680x1050. Which is the optimum resolution. I have the Geforce GT 220.

Regards.

---

### Post by wojox on 2011-04-23
Run in the terminal and post back:

```
xrandr
```

---

### Post by GenghisMcB on 2011-04-23
grahamtechnical:
   I did indeed get an nvidia X-server settings utility, which was the slight improvement I was talking about - that was what enabled up to 1360x768 rather than 1024x768.  It doesn't, however, offer anything higher than that, hence my suspicion that the problem lies with the monitor rather than the graphics card.

wojox:
   xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1152 x 864, maximum 1152 x 864
default connected 1152x864+0+0 0mm x 0mm
   1152x864       50.0* 
   1024x768       51.0  
   800x600        52.0     53.0     54.0  
   680x384        55.0     56.0  
   640x480        57.0  
   512x384        58.0  
   400x300        59.0  
   320x240        60.0

---

### Post by GenghisMcB on 2011-04-27
Any ideas?

---

