---
title: "DVB-T Cinergy T Stick Mini"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by tduccuong on 2010-11-08
hi all,

i've bought a dvb-t stick today, a Cinergy Mini. I pluged the stick into my ubuntu maverick box, but the system did not recognize it. I installed linux tv from this: hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb). But the system still did not recognize the stick.

Has anyone some experience with this dvb-t stick?

Thanks a lot!

---

### Post by LowSky on 2010-11-09
please open a terminal and type

```
lsusb
```
pleas epost the output here.

if the device is listed than we know the system can see it. it might be listed as the chipset. Sometimes the model is shared among multiple companies and support is easy to find, sometimes its not. I looked on the Mythtv Wiki and didn't find it listed, but even so that doesn't mean much as new tuners come out all the time based on older chips that work great.

---

### Post by tduccuong on 2010-11-10
hi LowSky, thanks for ur reply. Here is my lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device
Bus 003 Device 002: ID 1bcf:05cf Sunplus Innovation Technology Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 048d:9135 Integrated Technology Express, Inc. 
Bus 001 Device 005: ID 04f2:b090 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0c0b:b159 Dura Micro, Inc. (Acomdata) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It is the "Integrated Technology Express Inc". What should I do next?

---

