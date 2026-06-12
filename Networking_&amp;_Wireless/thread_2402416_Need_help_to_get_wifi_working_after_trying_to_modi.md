---
title: "Need help to get wifi working after trying to modify drivers"
date: 2018-09-29
forum: Networking &amp; Wireless
---

### Post by sbfueveday on 2018-09-29
Copy pasted code into terminal from this website : [https://dhalperi.github.io/linux-80211n-csitool/installation.html](https://dhalperi.github.io/linux-80211n-csitool/installation.html)
was halfway done before I realized wifi stopped working. Want to reverse any changes made.

---

### Post by chili555 on 2018-09-29
Wow! Heady, dangerous and complicated looking stuff. I suspect that it is obsolete and not applicable to your case. Notice that it says:> These instructions are currently expected to work on Linux operating systems that are based on an upstream Linux kernel version between 3.2 (e.g. Ubuntu 12.04) and 4.2 (e.g. Ubuntu 14.04.4).I suspect that your kernel version is newer thatn 4.2. Check:```
uname -r
```I think your kernel version is 4.4 or even newer.

Let's try:```
sudo rm /etc/modprobe.d/csitool.conf
sudo modprobe iwlwifi
sudo modprobe iwldvm
```Is your wireless working?

It may take a reboot.

---

### Post by sbfueveday on 2018-09-29
Thanks a ton chilli555!! wifi started working again!

I wanted to install csi drivers for a college project, didn't check the kernel version before doing so..

Yes my kernel version is 4.4 specifically :

```
$ uname -r
4.4.0-135-generic
```



just fyi sudo modprobe iwlwifi and the last instruction returend errors..


```
$ sudo modprobe iwlwifi
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/rt18723be.conf line 1: ignoring bad line starting with 'opions'
$ sudo modprobe iwldvm
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/rt18723be.conf line 1: ignoring bad line starting with 'opions'
```


Thanks for your help anyways!


I have one other issue thats been bugging me for a long time. If i should create a new thread, do let me know. Ever since i installed ubuntu on my hp laptop running windows 10, WiFi functionality has been aternating between windows and ubuntu. i.e., if it connects and works on windows, it stops wotking for ubuntu (even though it connected) and vice versa. Any idea what i should do to get it working on both OSs?

---

### Post by chili555 on 2018-09-29
> libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/rt18723be.conf line 1: ignoring bad line starting with 'opions'You haven't any rtl8723be device and so you may safely delete the file:```
sudo rm  /etc/modprobe.d/rt18723be.conf 
```> I have one other issue thats been bugging me for a long time. If i should create a new thread, do let me know. Ever since i installed ubuntu on my hp laptop running windows 10, WiFi functionality has been aternating between windows and ubuntu. i.e., if it connects and works on windows, it stops wotking for ubuntu (even though it connected) and vice versa. Any idea what i should do to get it working on both OSs?That suggests to me that one of the OSs leaves the device in a condition from which it cannont recover except to reboot into that OS and restart it.

Is there any Wake on WLAN setting in Windows? [https://docs.ubuntu.com/core/en/stacks/network/network-manager/docs/reference/snap-configuration/wowlan](https://docs.ubuntu.com/core/en/stacks/network/network-manager/docs/reference/snap-configuration/wowlan) If so, I'd try changing it from whatever it is to whatever it isn't; that is On to Off or Y to N, etc. or vice versa.

Is the result the same if you always cold boot rather than reboot?

Are you also looking for guidance about how to run a 4.2 kernel and resume your project?

---

### Post by sbfueveday on 2018-10-07
Hi, sorry for the late reply.

Yes i am looking for guidance on how to run 4.2 kernel. I'm willing to try out whatever you suggest. If this doesnt work out, we (our project team) are also looking into CSI drivers to run on raspberry pi. If 4.2 doesnt work put that is...

Any help would be appreciated, thank you.

---

### Post by chili555 on 2018-10-11
I suggest that you download and install the mainline 4.2 kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-wily/)

Notice that the packages are available for i386 (32-bit) and amd64 (64-bit). Find out which you need with:```
arch
```64-bit returns x86_64.

Assuming that is what you have, you would then need: 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-wily/linux-headers-4.2.0-040200-generic_4.2.0-040200.201510260713_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-wily/linux-headers-4.2.0-040200-generic_4.2.0-040200.201510260713_amd64.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-wily/linux-headers-4.2.0-040200_4.2.0-040200.201510260713_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-wily/linux-headers-4.2.0-040200_4.2.0-040200.201510260713_all.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-wily/linux-image-4.2.0-040200-generic_4.2.0-040200.201510260713_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-wily/linux-image-4.2.0-040200-generic_4.2.0-040200.201510260713_amd64.deb)

Install them all with:```
sudo dpkg -i linux*.deb
```Reboot. You may need to select 4.2 at the GRUB menu to keep from booting into your usual kernel, 4.4.0-135-generic.

> was halfway done before I realized wifi stopped working. For sure, when you unload the driver for your wireless device, the wireless will stop working. Of course and ideally, it will start working again when you modify and reload the now modified driver.

I know nothing about CSI Tool, so I don't know if the process is sound. This post is intended only to get you started with a 4.2 kernel.

---

