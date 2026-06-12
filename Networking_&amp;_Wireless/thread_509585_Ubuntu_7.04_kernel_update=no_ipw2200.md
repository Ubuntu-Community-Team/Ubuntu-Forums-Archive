---
title: "Ubuntu 7.04: kernel update=no ipw2200"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by alexgj on 2007-07-25
Hello! I call for your help, because im really lost (and desperate)... I have installed Ubuntu 7.04 in a Sony VAIO VGN-FS415S, and it worked flawlessly until i updated the kernel to 2.6.22.1. After that, the wifi adapter dissapeared from the system.

dmesg says:

alejandro@vaio:/lib$ dmesg | grep ipw
[   18.704000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0k
[   18.704000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   18.704000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   18.764000] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   18.764000] ipw2200: Unable to load firmware: -2
[   18.764000] ipw2200: failed to register network device
[   18.764000] ipw2200: probe of 0000:06:04.0 failed with error -5

Is there something i can do to resurrect it? I tried reloading the modules ipw2200 and ieee80211, but nothing happened. 

Thanks a lot in advance

Alejandro

---

### Post by tama on 2007-07-25
You need the restricted modules to make ipw2200 work.
You say you're using now a 2.6.22 kernel. Is it a custom kernel or are you using Gutsy packages?

If you're using a custom kernel, [here]("https://wiki.ubuntu.com/KernelCustomBuild") you can find a guide to build your kernel and its restricted modules.

If you're using Gutsy packages (officially discouraged) you'll have to install the linux-restricted-modules and linux-ubuntu-modules for your kernel version.

Anyway, are you sure you need the latest kernel?? You can do well with Feisty kernels if everything was ok.

---

### Post by alexgj on 2007-07-25
Thanks for answering! I downloaded the kernel from kernel.org and compiled it because i was having a lot of trouble with the nvidia driver. Big mistake! I need nothing of the new kernel.  I think i will reinstall from scratch...

Thanks for your help, much appreciated!

Alejandro

---

