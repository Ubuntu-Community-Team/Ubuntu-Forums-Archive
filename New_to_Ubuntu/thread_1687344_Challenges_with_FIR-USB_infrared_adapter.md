---
title: "Challenges with FIR-USB infrared adapter"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by Dreante on 2011-02-13
So as usual, I've tried to do my due diligence and have got lost with all the various tutorials and manual pages... from what I understand this shouldn't bee that difficult of an operation, so I must be missing the forest for the trees. Or some similar more appropriate analogy.

Anyhow, I've got an ACT-IR2000U Infrared USB dongle which I'm trying to hook up to my Lucid install.

I've installed irda-utils and lirc, and *think* I've followed all the steps correctly, but when I get to 'irdadump' I don't get any response.

Here's some obligatory terminal stuffs:

lsusb
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 003 Device 002: ID 09c4:0011 ACTiSYS Corp. ACT-IR2000U IrDA Dongle**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


dmesg | grep irda
```

[   13.800556] irda_init()
[   14.984445] irda_usb_parse_endpoints(), And our endpoints are : in=02, out=01 (64), int=03
[   14.986720] irda_usb_init_qos(), dongle says speed=0x13E, size=0x20, window=0x2, bofs=0x4, turn=0x2
**[   14.988226] IrDA: Registered device irda0**
[   14.988268] usbcore: registered new interface driver irda-usb

```


ifconfig irda0
```

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

If I do irdadump, push remote control buttons and try sending it codes from an old nokia, my understanding was I should be seeing something?!

Any clues?

-CD

---

### Post by Dreante on 2011-02-14
Bump?

---

