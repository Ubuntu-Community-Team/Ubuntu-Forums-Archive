---
title: "sound not working"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by Geek-abor on 2010-12-27
i have a problem with my sound,i had instaled ubuntu with wubi and it worked without any problem but now i have removed it and installed a fresh ubuntu 10.10 which is not with wubi, but now i don't have sound.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by karthick87 on 2010-12-27
Click sound applet in your panel and goto preferences>>output and be sure that it is not muted..

---

### Post by vacc73 on 2010-12-31
> **Geek-abor said:**
> i have a problem with my sound,i had instaled ubuntu with wubi and it worked without any problem but now i have removed it and installed a fresh ubuntu 10.10 which is not with wubi, but now i don't have sound.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
if karthick87's suggestion doesn't work, go into alsa mixer, and if you haven't intalled it , install it. Then make sure nothing is muted there and everything is turned on, sinc'd and volume adjusted. Then go from there

---

