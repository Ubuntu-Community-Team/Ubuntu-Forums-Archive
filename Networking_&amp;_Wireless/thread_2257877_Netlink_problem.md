---
title: "Netlink problem"
date: 2014-12-23
forum: Networking &amp; Wireless
---

### Post by wei5 on 2014-12-23
Dear All

I am new to Ubuntu.
As i was trying to compile a driver there is a issue I don't know how to solve.
While compiling, when it gets to wpa_supplicant it will stop and have this message output.

> In file included from ../src/drivers/driver_nl80211.c:20:0:
/usr/include/netlink/genl/genl.h:15:29: fatal error: netlink/netlink.h: No such file or directory
compilation terminated.

I did installed the libn-1.1.4. 
And also tried to look up the file "driver_nl80211.c". But there is no "netlink/netlink.h" inside.

Thank you!

---

### Post by chili555 on 2014-12-23
I suggest you do:```
sudo apt-get install libnl-dev libnl1 
```And then try again.

I am very interested in what driver you are installing that requires that you compile wpa-supplicant from source. I am quite confident that there is a better way. We would hate for you to go to all this trouble needlessly.

---

### Post by wei5 on 2014-12-23
Hi chili555
I have tried this already but the problem still stands.
I am trying to compile a ath6kl driver actually...
It is given me such a headache...

---

### Post by chili555 on 2014-12-23
The driver ath6kl is present in kernel versions 3.13 and later; that roughly means Ubuntu 14.04 and later. It can be compiled pretty easily from backports. What Ubuntu version are you using?

Does your device not work because it simply lacks firmware?```
$ modinfo drivers/net/wireless/ath/ath6kl/ath6kl_usb.ko
filename:       /home/chili/Desktop/Forum/backports-3.18-rc1-1/drivers/net/wireless/ath/ath6kl/ath6kl_usb.ko
[COLOR="#FF0000"]firmware:       ath6k/AR6004/hw1.3/bdata.bin
firmware:       ath6k/AR6004/hw1.3/bdata.bin
firmware:       ath6k/AR6004/hw1.3/fw.ram.bin
firmware:       ath6k/AR6004/hw1.2/bdata.bin
firmware:       ath6k/AR6004/hw1.2/bdata.bin
firmware:       fw.ram.bin
firmware:       ath6k/AR6004/hw1.1/bdata.DB132.bin
firmware:       ath6k/AR6004/hw1.1/bdata.bin
firmware:       fw.ram.bin
firmware:       ath6k/AR6004/hw1.0/bdata.DB132.bin
firmware:       ath6k/AR6004/hw1.0/bdata.bin
firmware:       fw.ram.bin[/COLOR]
license:        Dual BSD/GPL
description:    Driver support for Atheros AR600x USB devices
<snip>
```Check:```
sudo modprobe ath6kl_usb
dmesg | ath
```

---

### Post by wei5 on 2014-12-25
Thanks for the advises
My Ubuntu version is 12.04 LTS.
Actually my main goal is to use the cross-compiler and made a ath6kl driver from a x86 system to a ARM based system.
Do you have any idea how can I do that?
I tried to modify the MAKEFILE change the gcc to arm-linux-gnueabi-gcc. I thought it could force it to compile a ARM based ath6kl driver for me... Is this direction correct or wrong? Please help.....

---

### Post by chili555 on 2014-12-25
> **wei5 said:**
> Thanks for the advises
My Ubuntu version is 12.04 LTS.
Actually my main goal is to use the cross-compiler and made a ath6kl driver from a x86 system to a ARM based system.
Do you have any idea how can I do that?
I tried to modify the MAKEFILE change the gcc to arm-linux-gnueabi-gcc. I thought it could force it to compile a ARM based ath6kl driver for me... Is this direction correct or wrong? Please help.....I know little or nothing about cross-compiling and ARM, so please understand I am guessing a bit here.

I'm not sure what package you are working with but I like backports: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/)

I saw this: [https://backports.wiki.kernel.org/index.php/Documentation/packaging#Usage_guide](https://backports.wiki.kernel.org/index.php/Documentation/packaging#Usage_guide)> Cross compiling

To cross compile:
```
set -a
CROSS_COMPILE=${CROSS_COMPILE}
ARCH=${TARGET_CPU}
KLIB_BUILD=${DEV_PATH}/${LINUX_DIR}
KLIB=${TARGET_ROOT_ON_HOST}
set +a
make oldconfig  # menuconfig worked here too
make
make install
```
The 'make install' target isn't currently sane for cross-builds due to the bacport_firmware_install script not respecting prefixes. For now you can comment out that script few others like initrd updates, from being run out of the Makefiles.And this: [http://stackoverflow.com/questions/18855554/linux-wifi-backports-cross-compile](http://stackoverflow.com/questions/18855554/linux-wifi-backports-cross-compile)  Please see the answer with three up-votes. In your case, you would make defconfig-athk6l and don't forget the firmware.

That's it! That's all and maybe more than I know.

---

