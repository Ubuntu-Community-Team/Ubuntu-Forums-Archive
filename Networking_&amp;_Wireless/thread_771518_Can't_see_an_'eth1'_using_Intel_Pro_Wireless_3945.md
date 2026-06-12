---
title: "Can't see an 'eth1' using Intel Pro Wireless 3945"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by herchu on 2008-04-27
Hi,
I am using Ubuntu 7.10 on a T61. I have been running **ipw3945** (restricted drivers enabled) and everything worked fine. I also ran **nvidia-glx-new**.

I needed to upgrade nvidia driver (100.x) to latest from Nvidia site (169.x), using binary installer, trying to solve some issues with video. To make it work, I removed packages **nvidia-glx-new** and **nvidia-kernel-common[B] (otherwise, the nvidia driver installed at boot would still be 100.x). This also uninstalled [B]linux-restricted-modules-2.6.22.14-generic**.

Now, after boot I have no interface eth1. I suspect the problem is having restricted drivers disabled (In KDE System Settings -> Advanced -> Restricted Drivers it complains with a popup about missing the linux-restricted-modules-2.6.22.14-generic package). 

How can I re-enable or run the ipw3945 (I don't know what is failing exactly)? Reinstalling the missing package also reinstalls nvidia-kernel-common, which I don't want to have installed.

If it helps, here is the output of **dmesg | grep ipw3945**
```
[   19.520000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   19.520000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.520000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
```
(I think there used to be an extra line about 'detecting geography')

and **lsmod | grep ipw**:
```
ipw3945               119840  0
ieee80211              35656  1 ipw3945
```

however **ifconfig** only shows 'lo' and 'eth0', and I used to see an 'eth1' there. Please tell me if more logs are needed.

Any idea to re-enable it? Thanks a lot!

---

### Post by herchu on 2008-04-28
Ok, the problem solved itself. I did NOT uninstalled nvidia-kernel-common and linux-restricted-modules-*, but instead blacklisted only the nvidia driver from being loaded -- so wireless works perfectly now.

---

### Post by SadaraX on 2008-04-28
Is there a particular reason you are not using Ubuntu/Kubuntu 8.04 and are still using 7.10?

---

