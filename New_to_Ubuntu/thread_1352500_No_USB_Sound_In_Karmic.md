---
title: "No USB Sound In Karmic"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by spikoley on 2009-12-11
The USB sound is not working in Karmic Koala.  I am not sure where to start trouble shooting.

aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0x47f0xad01 [USB Device 0x47f:0xad01], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


---

### Post by spikoley on 2009-12-11
I fixed it and it was easy.  Just install Backports.

```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

---

