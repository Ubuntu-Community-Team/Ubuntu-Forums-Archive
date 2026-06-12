---
title: "Belkin F5D8053v3 is it rt2870 ?"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by Jackie999 on 2008-09-18
I'm having a heck of a time getting the ralink linux driver to work with my USB wireless-in fact it just doesn't work for me. The ndiswrapper freezes me using the windows .inf files that came with the device, and the native drivers just won't show the ra0 device.
My question...even though the windows drivers are named rt2870.xxx is it possible these 'v3' versions of the stick (there is also a 'v1') have a different chip that, for windows purposes, works okay with the rt2870 driver but is a no go with the linux driver?

Was reading serialmonkey and came across this post which makes me go 'hmmmm....'
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=6&t=4884&hilit=F5D8053](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=6&t=4884&hilit=F5D8053)

I could crack it open and read the chip but I'm not sure if that would ruin it...

---

### Post by jakob.g on 2009-03-27
this reply is a bit late, but you need to recompile the rt2870 module because it's missing the USB ID für F5D8053v3. the following patch needs to be included:

--- old/src/linux-2.6.29/drivers/staging/rt2870/rt2870.h	2009-03-24 00:12:14.000000000 +0100
+++ new/src/linux-2.6.29/drivers/staging/rt2870/rt2870.h	2009-03-27 21:18:12.000000000 +0100
@@ -104,6 +104,7 @@
 	{USB_DEVICE(0x14B2,0x3C07)}, /* AL */			\
 	{USB_DEVICE(0x14B2,0x3C12)}, /* AL */           \
 	{USB_DEVICE(0x050D,0x8053)}, /* Belkin */		\
+	{USB_DEVICE(0x050D,0x815C)}, /* Belkin */		\
 	{USB_DEVICE(0x14B2,0x3C23)}, /* Airlink */		\
 	{USB_DEVICE(0x14B2,0x3C27)}, /* Airlink */		\
 	{USB_DEVICE(0x07AA,0x002F)}, /* Corega */		\

the location of rt2870.h varies.. you can try 

grep -e 050D, -f $(find source_dir/)

to find it

---

