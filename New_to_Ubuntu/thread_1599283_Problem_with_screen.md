---
title: "Problem with screen"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by sporadic999 on 2010-10-17
I just installed ubunto 10.10 (64 bit) on my PC with a SIS761GX graphics card and a e-yama 17NE screen. The X configuration is close to good - the screen fits etc. But I have vertical interference lines running down the screen (columns of pulsing horizontal lines) that get worse if I move windows around the screen.

Below is the output from xrandir 

The rates of 60.0 and 75.0 are within the range of the screen (24 to 83 & 55 to 76). I am not sure what the  significance of the asterisk in 60.0*.

Any clues on how I go about trying to fix this.

The screen works fine under windows.

Thanks

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      60.0*    75.0  
   1280x960       60.0  
   1280x854       75.0     60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     70.0     60.0  
   1024x576       75.0     60.0  
   960x600        60.0  
   832x624        75.0  
   960x540        60.0  
   800x600        75.0     72.0     60.0     56.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0  
   848x480        60.0  
   800x480        75.0     60.0  
   720x480        61.0  
   640x480        75.0     73.0     67.0     60.0  
   720x400        70.0  
   640x400        72.0  
   512x384        60.0  
   400x300        60.0  
   320x240        61.0

---

### Post by cfsterpka on 2010-10-18
I'm having the same issues with xrandr after the upgrade... Though I don't have vertical lines, I just have a 640x480 resolution on my monitor which I can't change.  I'm using the Nvidia binary drivers (tried both the ones through Synaptic and also the latest one's from NV's site).

In 10.04 I was able to fix the resolution issue by using xrandr, as it suggests in the Ubuntu NV help [page]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"), though now I can't because it doesn't list any devices...

I also tried stuff from the X config [page,]("https://wiki.ubuntu.com/X/Config/Resolution") but it's really hard to figure out how to get anything done on a 640x480 display!

(also Xorg -configure fails and dpkg-reconfigure doesn't seem to do anything)

---

### Post by cfsterpka on 2010-10-20
So I'm not sure if this will help you, but the resolution for me was to just create a file:
/etc/X11/xorg.conf.d/50-device.conf

and put the lines that would have gone in my xorg.conf for the "device" and "monitor" sections into it.  Using an xorg.conf didn't work for me, though supposedly it's supposed to work...

Are you using the open source or the vendor drivers?  It might be worth a try...

---

