---
title: "Acer ferrari 4005 edgy amd 64 wireless problem"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by nancom on 2007-03-07
I try to follow instruction that use  ndiswrapper from post in this forum. but i can't success to use my wireless. any one can help me.

---

### Post by n00b@linux on 2007-03-07
Run```
lspci
```
from a terminal and post the results so that we can see your hardware.
Also post the results of the following commands (each run separately):```
ifconfig
iwconfig
```

---

### Post by nancom on 2007-03-08
ok after i use ndiswrapper and blacklist bcm48xx. My ehternat card is only eth0 and lo.
but eth0 use for my wire lan. How to use for wireless . And my wireless led not blink.
on /var/log/dmesg show 


[   30.336688] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   30.441460] ndiswrapper (load_pe_images:573): fixing KI_USER_SHARED_DATA addr
ess in the driver
[   30.442539] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) load
ed
[   30.450643] ndiswrapper (NdisWriteErrorLogEntry:241): log: 761A39B0, count: 1
, return_address: ffffffff882e713e
[   30.450650] ndiswrapper (NdisWriteErrorLogEntry:244): code: 267
[   30.450705] ndiswrapper (miniport_init:264): couldn't initialize device: C000
0001
[   30.450712] ndiswrapper (pnp_start_device:428): Windows driver couldn't initi
alize the device (C0000001)
[   30.450728] ndiswrapper (miniport_halt:327): device ffff8100783a3500 is not i
nitialized - not halting
[   30.450737] ndiswrapper: device eth%d removed
[   30.450740] unregister_netdevice: device eth%d/ffff8100783a3000 never was reg
istered
[   30.450759] ndiswrapper: probe of 0000:06:02.0 failed with error -22


please help me.

---

