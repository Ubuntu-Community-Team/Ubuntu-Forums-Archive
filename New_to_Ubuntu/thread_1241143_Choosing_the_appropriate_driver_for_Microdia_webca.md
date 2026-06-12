---
title: "Choosing the appropriate driver for Microdia webcam"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by Julita on 2009-08-15
Hello! I have installed necessary driver for my card, but v4l-info shows 

```
  driver                  : "sonixj"
	card                    : "USB camera"
	bus_info                : "0000:00:07.2"
	version                 : 2.3.0
	capabilities            : 0x5000001 [VIDEO_CAPTURE,READWRITE,STREAMING]
```

I need sn9c20x.ko instead of sonixj... My camera doesn't work, and after running xawtv on terminal the error is

```
xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.28-15-generic)
xinerama 0: 1152x864+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
```

---

### Post by Humanum on 2009-08-15
Is your cam integrated on your laptop or not ???

---

### Post by R_W322 on 2009-08-15
didn't notice that was a webcam disregard my post.

RYAN.WDZIECZNY

---

### Post by Julita on 2009-08-15
My cam is not integrated; it connects via USB. SDCARD is not used with it. Thank you!

---

