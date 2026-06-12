---
title: "NDISwrapper help and questions on a Buffalo USB device"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by ZeroXR on 2007-05-31
My sister's tower has a Buffalo USB wifi device and I was just wondering what file to I point NDISwrapper to use for the device...

The Buffalo support archive has a zip containing the drivers and all, but here's what is inside the zip:
```
bwcdrv.cat  BWCINST.dll   netusg54.inf  rndismpw.sys  usb8023w.sys
bwcdrv.sys  netbwc2k.inf  RNDISMPK.sys  usb8023k.sys  wliusg54.cat
BWCDRV.VXD  netbwc98.inf  rndismpm.sys  usb8023m.sys

```

Which one do I use? She's curious about Ubuntu, but to her she needs the net access. Anyone want to shed some light?

---

### Post by adampyre on 2007-05-31
I'm betting the netusg54.inf is one that you need as the other .inf's seem to indicate they are for 98 and 2000, and the .sys might match the model number of your device? As for the .cat, if needed, i'm not certain. I'd try to find out which .sys and try it with just the .inf and .sys....... but now that i think of it, if you go with the .inf I say, it may automatically use the correct files otherwise? If you want, just try and install netusg54.inf and if it doesn't work, uninstall and try again.....

---

