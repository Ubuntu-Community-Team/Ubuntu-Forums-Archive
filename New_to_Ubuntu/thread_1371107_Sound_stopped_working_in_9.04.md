---
title: "Sound stopped working in 9.04"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by davidside on 2010-01-03
I started the computer earlier today and none of the USB ports were working. I restarted the computer and the USB ports were fine but the sound stopped working. Instead of the drum sound at the beginning, I get a static crackling sound. I get the same thing when I try to play a song or a Youtube video. I restarted the computer several times but no luck. I should also mention that I installed and the uninstalled MySQL but I'm not sure if that has to do with anything.

Also, one of the times I restarted, I received this error message:
usb 3-2, device descriptor read/64, error -110

Thanks for any help!

---

### Post by duanedesign on 2010-01-04
Your problem is most likely because your PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
alsamixer -Dhw
```

---

