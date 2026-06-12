---
title: "screen rez problem on new 10.04 lts 64 bit install"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by tekno62 on 2010-05-03
I just down loaded the Ubuntu 10.04 LTS 64 bit and when I try to try the new Ubuntu, test the memory or check the disk I get an "out of range" error on my screen


Gforce 9800 Gt with an older GEM GL-715A its max rez is 1024 X 768

thanks:confused:

---

### Post by nhasian on 2010-05-03
i think the problem can be resolved by installing the restricted nvidia drivers instead of using the open source one.  

if you are testing ubuntu with a usb thumbdrive (not a cd) you can install the drivers by going to system-> administration-> drivers

or you can manually install them in a terminal with:

```
sudo apt-get install nvidia-current
```

good luck

---

### Post by tekno62 on 2010-05-03
thanks - its on a CD.

---

### Post by oldsoundguy on 2010-05-03
An FYI .. some issues with the Nvidia driver FROM Nvidia.  Have it working on two standard aspect screens and all bells and whistles work fine including rotation .
HOWEVER .. on my wide aspect ratio, the rotate mysteriously disappeared from the item list in the Nvidia control screen .. and the resolution did not go HIGH enough .. so am running the default Ubuntu driver (resolution MUCH better) .. but, NO option in the default to rotate (RandRRotation true - added to xorg does not work!)
Let us hope Nvidia gets it right soon on their restricted driver!!

---

