---
title: "Intel Dual Band Wireless-AC 3168NGW - this device is not working"
date: 2020-05-21
forum: Networking &amp; Wireless
---

### Post by liubomirwm on 2020-05-21
Hi, i see a message "This device is not working" in the Additional drivers section of the Ubuntu Software Updater. I'm using Ubuntu 20.04 LTS. Please see the screenshot: [COLOR=unset][https://imgur.com/aexn5jd](https://imgur.com/aexn5jd)[/COLOR]
I have not manually installed a driver. I have Wi-Fi, haven't noticed problems. What does this mean?

---

### Post by liubomirwm on 2020-06-05
Anyone can help me?

---

### Post by Yellow Pasque on 2020-06-06
> I have Wi-Fi, haven't noticed problems

Then it would appear to be a bug or issue with the "Additional Drivers" GUI. Annoying, but harmless if the wi-fi works. 
Just to be clear: you only have one wireless adapter, correct?

>  I'm using Ubuntu 20.04 LTS. 

Clean install or upgrade from previous version?

---

### Post by jeremy31 on 2020-06-06
Moved to Networking & Wireless

The backport-iwlwifi-dkms will show up in the driver manager if your Intel wifi cards ID matches one of them in the modalias section of the package list.  The problem is that a lot of those ID's are actually working with the kernels version of iwlwifi

---

### Post by liubomirwm on 2020-06-07
> **Yellow Pasque said:**
> Just to be clear: you only have one wireless adapter, correct?
I think so.
```
lspci | grep -i net
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
Network controller: Intel Corporation Dual Band Wireless-AC 3168NGW [Stone Peak] (rev 10)
```
> **Yellow Pasque said:**
> Clean install or upgrade from previous version?
Upgrade from 19.10

---

### Post by Yellow Pasque on 2020-06-07
As I speculated and jeremy31 confirmed, it is just a cosmetic bug with the Additional Drivers GUI.
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1859308](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1859308)

---

### Post by liubomirwm on 2020-06-07
Okay, thank you very much. I marked as affected in Launchpad.

---

