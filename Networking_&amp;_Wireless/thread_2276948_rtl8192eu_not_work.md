---
title: "rtl8192eu not work"
date: 2015-05-05
forum: Networking &amp; Wireless
---

### Post by kevin163 on 2015-05-05
since the kernel upgrade to 4.0.1, because I had a version 3.1x, when
 you update the driver rtl8192eu not work for me, I get the following 
error

 ```
make [1]: *** [_module_ / home / kevin / Desktop / install_folder / driver / rtl8192EU_linux_v4.2.2_7585.20130524] Error 2
make [1]: Leaving directory '/usr/src/linux-headers-4.0.1-040001-generic'
Makefile: 1043: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile driver make mistake: 2
Please check mistake Mesg
```


I tried to go back to the kernel version 3.1x but the problem persists
 you could do, not much information about this device chipset is 0bda: 
818b

otherwise
 when compiling the 4.0.1 kernel drivers looking in the menuconfig 
meeting almost every family realtek drivers 8192ex, 8192eu least, is 
why? Please I need help I've been almost a week with this


the end of the log output (not copy everything because they are almost 500 lines) is as follows

```
cc1: some errors as warnings Being Treated
make [2]: *** [/home/kevin/Escritorio/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/li$
make [1]: *** [_module_ / home / kevin / Desktop / install_folder / driver / rtl8192EU_linux_v4.2.2_7585.20130524] $
make: *** [modules] Error 2

```
I need help

---

### Post by wildmanne39 on 2015-05-06
Please make sure you have everything installed to compile the new driver.
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
```
watch for errors.

Link to where you got the driver?
It may be to old a driver for this new of a kernel and it is possible that there is not a driver for this kernel yet.
Thanks

---

### Post by Pilot6 on 2015-05-06
This kernel is too new for that driver. But it looks that good drivers are already there.
You do not need to install anything.

---

