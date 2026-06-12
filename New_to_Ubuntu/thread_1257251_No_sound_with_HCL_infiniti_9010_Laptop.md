---
title: "No sound with HCL infiniti 9010 Laptop"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by lovelyvik293 on 2009-09-03
I have a HCL infiniti 9010 Laptop.I installed Ubuntu 9.04.All things are working fine except the sound driver.Please guide me how to enable the sound system.I already checked the alsamixer,but with no success.

---

### Post by taavikko on 2009-09-03
Please post the output of
```
aplay -l; grep -i codec /proc/asound/card0/codec#0
```

---

### Post by lovelyvik293 on 2009-09-04
```

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
grep: /proc/asound/card0/codec#0: No such file or directory

```

---

