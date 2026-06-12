---
title: "problem with video card driver and 10.04"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by lupulin on 2010-10-31
I seem to be having a run of bad luck or stupidity lately. I tried to activate a driver for the nvidea card I have been using succesfully for the past few weeks. After activating the driver the computer gives me an error. Says running in low graphics mode (EE)no devices found. I click ok and then it brings me to a blank menu where I can click ok or cancel. Either option takes me to a black screen. I can get to the grub command line if I can fix things from there. Any help would be appreciated.

---

### Post by lupulin on 2010-10-31
Ok I was able to figure out that the blank menu was actually just off the screen. I manually 'auto-adjusted' the monitor and selected troubleshoot problem and then chose to use my previous configuration.

It does seem like I have some issues with my video card/drivers. Any tips on configring my settings? I'm a bit in the dark. when I use ```
 lspci | grep VGA 
``` it tells me:

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
01:01.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

I appear to also still be using driver version 173 which is what caused the error to begin with.

---

