---
title: "Unable to Update X"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by rosehipzero on 2010-12-11
Im trying to install the latest nVidia drivers for Maverick but am unable to do so. 0 AD is demanding that i update to the latest drivers and when i go to install them, it wont let me

this what i am doing, tell me if im doing something wrong please
```
/home/user/Download
sudo sh NVIDIA-Linux-x86-260.19.21.run
```

I tried that, but the installer says to kill X server. so i tried 
```
killall X
```

but it says there is no resource X. How do i kill X server properly?

---

### Post by TeoBigusGeekus on 2010-12-11
X server must not run in order to update your graphics card driver.
&#914;&#959;&#959;t into recovery mode, choose root terminal, navigate to the driver's location and try again.

---

### Post by rosehipzero on 2010-12-11
thanks, i thought there was another way then that, but i guess i have no choice =/

THanks though!

---

