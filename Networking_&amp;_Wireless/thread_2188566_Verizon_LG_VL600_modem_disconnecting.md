---
title: "Verizon LG VL600 modem disconnecting"
date: 2013-11-17
forum: Networking &amp; Wireless
---

### Post by nuser on 2013-11-17
I've been trying to get the VL600 modem on linux (3.6.11 kernel).

```
lsusb |grep LG
Bus 001 Device 004: ID 1004:61aa LG Electronics, Inc.

```
In /var/log/messages I can see that it recognizes it:
```
kernel: [    6.948485] cdc_acm 1-1.2:1.2: ttyACM0: USB ACM device
kernel: [    7.102020] usbcore: registered new interface driver cdc_ether
kernel: [    7.115306] usbcore: registered new interface driver cdc_acm
kernel: [    7.231864] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
kernel: [    7.252092] lg-vl600 1-1.2:1.0: wwan0: register 'lg-vl600' at usb-bcm2708_usb-1.2, LG VL600 modem, 64:99:5d:fa:f7:fa
kernel: [    7.402915] usbcore: registered new interface driver lg-vl600

```

```
lsmod|grep lg
lg_vl600                3058  0
cdc_ether               4750  1 lg_vl600

```

I've tried setting up wvdial but with no luck, same with sakis3g. The only thing that has worked for me is the attach script from [https://github.com/balrog-kun/LG-VL600-utils/tree/master](https://github.com/balrog-kun/LG-VL600-utils/tree/master) . It connects fine (starts blinking green), however, some time after connecting it disconnects (and starts blinking blue). The adapter stays up and the IP address is still set but the connection is useless.

Any thoughts on how to fix this or get it working with wvdial? Anyone got this modem working reliably? Alternately, is there a way for me to detect when it's gone down so i can at least reconnect automatically?

Thanks!

---

