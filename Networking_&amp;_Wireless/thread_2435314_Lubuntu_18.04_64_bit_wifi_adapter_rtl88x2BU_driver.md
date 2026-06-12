---
title: "Lubuntu 18.04 64 bit: wifi adapter rtl88x2BU driver problem"
date: 2020-01-19
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2020-01-19
Hi,
I have lubuntu 18.04 64 bit with a wifi adapter rtl88x2BU. The adapter worked well up to yesterday with this [driver]("https://github.com/its-izhar/rtl88x2bu-driver") (patched version) when I was using the linux kernel v5.0.x. After an update to the version v5.3.x I cannot compile the driver anymore. So after some searches on the Web I found that [this]("https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959") driver should work. However, it does not work and I have an error on boot.
```
Failed to start Load Kernel Modules
See 'systemctl status systemd-modules-load.service' for details
```

The module 88x2bu.so is the one related to the rtl88x2BU.

Any idea?
Thank you

---

### Post by jeremy31 on 2020-01-19
Moved to Networking

Please see the wireless script link in my signature and post results

---

### Post by erotavlas on 2020-01-19
Thank you for your reply.
[This]("https://paste.ubuntu.com/p/QBhkPxTwcW/") is the link with the code.

---

### Post by jeremy31 on 2020-01-19
And results for ```
dmesg | grep 88x2bu
```

---

### Post by erotavlas on 2020-01-19
```
dmesg | grep 88x2bu
[   13.027381] 88x2bu: loading out-of-tree module taints kernel.
[   13.028498] 88x2bu: module verification failed: signature and/or required key missing - tainting kernel
[   13.032113] RTW: rtl88x2bu v5.6.1_30362.20181109_COEX20180928-6a6a
[   13.032114] RTW: rtl88x2bu BT-Coex version = COEX20180928-6a6a
[   13.339850] usbcore: registered new interface driver rtl88x2bu
[   13.433976] rtl88x2bu 3-4:1.0 wlx1cbfce35251b: renamed from wlan0
```

Now the wifi adapter is working even if the led does not blink. I do not know the reason.

---

### Post by erotavlas on 2020-01-20
Any suggestion about how to remove the error message?

---

