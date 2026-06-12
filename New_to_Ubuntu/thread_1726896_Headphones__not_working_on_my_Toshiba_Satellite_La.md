---
title: "Headphones  not working on my Toshiba Satellite Laptop"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by conualfy on 2011-04-11
I could see that some users got their headphones working, but on this Toshiba Satellite C650-16R I can not use the headphones. Sound only gets from the laptop speakers.

This is what I get from aplay -l:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by conualfy on 2011-04-11
Found the solution in another thread, hope it will help others too:

The solution for other Toshiba laptop (L650, etc.) works for Satellite C650 too:



```
sudo gedit /etc/modprobe.d/alsa-base.conf
```add this in the end:

```
options snd-hda-intel model=thinkpad position_fix=1 enable_msi=1 
```

Enjoy the headphones!






> **conualfy said:**
> I could see that some users got their headphones working, but on this Toshiba Satellite C650-16R I can not use the headphones. Sound only gets from the laptop speakers.

This is what I get from aplay -l:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

