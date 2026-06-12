---
title: "Bluetooth mouse"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by stardustdk on 2008-05-20
Hey all.

I am running Ubuntu 8.04.

I have a usb bluetooth dongle and can get my Logitech headset to work, even as trusted.

But i can't get my logitech bluetooth mouse to work at all, even i try to follow the suggestions found in these forums???:confused:

I have installed about all bluetooth and bluez.....???

When i do a browse devices, it is found, but when i try to connect, i got this: 

> could not show "obex://xx:xx:xx:xx:xx:xx/".
Error: host down


My lsusb shows this:

> Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


What shall i do?

Best regards

Stardustdk

---

### Post by muadnu on 2008-05-20
I think the "browse devices" options is for when you want to see what's stored in a device to which you are connecting via bluetooth (e.g. a cellphone).

When I have trouble with my bluetooth mouse or keyboard, what always saves me is running

```
sudo hidd --search
```

I don't know if you tried this, and I'm not sure if the hidd command comes with bluez-utils or bluez-libs or I had it somehow installed, but you can give it a try for now...

---

### Post by stardustdk on 2008-05-20
And that did exactly the trick :).

Thanx

Stardustdk

---

