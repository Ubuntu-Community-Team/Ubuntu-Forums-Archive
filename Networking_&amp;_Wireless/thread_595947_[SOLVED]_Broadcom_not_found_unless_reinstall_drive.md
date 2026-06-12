---
title: "[SOLVED] Broadcom not found unless reinstall drivers in Vista first"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by shadowhywind on 2007-10-29
I am having a bit of a strange problem, that hopefully someone can help with. My wireless card, a broadcom 4312 will working perfectly in kubuntu gutsy up to the point where i reboot. then there is a small chance that when it comes back from the reboot, my wireless card is no longer found. If i boot into windows, vista, I notice that vista no longer sees my wireless card either. But if i reinstall the drivers in Vista, and reboot back into kubuntu my wireless card is working again. and then repeat the cycle. 
Steps I have tried so far: 
  1) I completeled Vista since it sucks, Kubuntu still couldn't see the wireless
 2) Reinstalled Vista *which may have killed me a little inside*, reinstalled the Drivers and So far Vista, and Kubuntu both see the wireless card. 
  3) dmesg | grep ndiswrapper comes up with this 
```
dmesg | grep ndiswrapper
[   36.719340] ndiswrapper version 1.48 loaded (smp=yes, preempt=no)
[   37.125543] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   37.127439] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   37.135165] ndiswrapper: using IRQ 10
[   37.498564] usbcore: registered new interface driver ndiswrapper

ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)

``` 

When kubuntu does not see the wireless card and i do ndiswrapper -l, all i get is bcmwl5 : driver installed. That is it, never the device present line. So any ideas. Because it would be nice not to have to go into vista to get my wireless working in kubuntu. Thanks!

---

### Post by shadowhywind on 2008-01-09
Well i solved my issue, It was due to a faulty motherboard, got it replaced and everything is back to normal.

---

