---
title: "Change Device ID for dongles"
date: 2015-05-31
forum: Networking &amp; Wireless
---

### Post by ritwik3 on 2015-05-31
Hi,

I am new to Ubuntu. I was wondering if it is possible to change the Device ID of Zte dongle to Huawei and vice-a-versa?

---

### Post by jeremy31 on 2015-05-31
I don't think that is possible but what exactly are you trying to accomplish?  Sometimes you can make a kernel module work with an unsupported device if it is USB by using [FONT=Consolas]/sys/bus/usb/drivers/<module-name>/new_id
[/FONT]

---

