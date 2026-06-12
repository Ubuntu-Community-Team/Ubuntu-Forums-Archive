---
title: "firefox causes erratic computer behavior"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by jmborr on 2011-06-07
The weirdest thing, opening firefox has diverse consequences. I have observed that sometimes:
1- firefox crashes
2- my ubuntu session dies
3- the computer reboots
3- the computer freezes

I updated firefox to v.4.0.1, I open it in safe-mode with all add-ons and plugins disabled, and I made sure that file /etc/nsswitch.conf contains no "wins" in the "hosts:" line. It all made no difference ](*,)

Any suggestion is greatly appreciated.

**Update**: "strace firefox" outputs the following line, among other stuff:
"*write(2, "firefox-bin": Fatal IO error 11 ("..., 84firefox-bin: Fatal IO error 11 (Resource temporarily unavailabe) on X server :0.0.) = 84*"
Maybe somebody can make sense out of this?

---

### Post by jmborr on 2011-06-07
The nvidia driver installed from "System->Administrator->Additional Drivers" was junk. I had to remove it first:
```
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
```

I downloaded the appropriate driver for my "PNY Verto GeForce FX 5500 AGP" graphics card, file "NVIDIA-LINUX-x86-173.14.30-pkg1.run".

Installation process:
1- Start session as "recovery console"
2- stop the X-server ```
sudo /etc/init.d/gdm stop
```
3- press Ctrl+Alt+F1 to bring about the login prompt, then login
4- make sure the NVIDIA install shell can build the drivers. ```
sudo apt-get install build-essential pkg-config
```
5- Install the driver:```
chmod a+x NVIDIA-LINUX-x86-173.14.30-pkg1.run
sh NVIDIA-LINUX-x86-173.14.30-pkg1.run
```
 the NVIDIA installation shell will ask a series of questions that you should accept.
6- restart the X-server ```
sudo /etc/init.d/gdm start
```

Presto! No more erratic behavior!!!
I hope this will be of help.

---

### Post by jmborr on 2011-06-14
I fixed firefox erratic behavior but later the computer persisted in freezin/rebooting.

The reason was that the "cool&quiet" of my AMD CPU feature in the BIOS, which was enabled. I had to disable this feature.

---

