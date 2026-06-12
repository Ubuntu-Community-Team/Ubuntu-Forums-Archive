---
title: "usb webcam in skype"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by nichos on 2011-07-15
Just discovered that although my usb webcam works with "cheese" it does not work in Skype.

In XP it worked OK in Skype.

Also where do I see the Ubontu version I am using here, like "About" is used elsewhere.

---

### Post by linuxyogi on 2011-07-15
> **nichos said:**
> Just discovered that although my usb webcam works with "cheese" it does not work in Skype.

In XP it worked OK in Skype.

Also where do I see the Ubontu version I am using here, like "About" is used elsewhere.


Plug in your Webcam, open Terminal & type

For 32 Bit Ubuntu

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

For 64 Bit Ubuntu

```
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype
```

Now  goto Skype's settings > Video & check if your Cam is working.

You must also mention you webcam's details

```
lsusb
```

To know your Ubuntu ver. 

```
lsb_release -a 
```

---

### Post by nichos on 2011-07-16
Thanx L.Yogi,

I typed this but it keeps bleenking for 30mnts, is it normal?
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype

And the " lsusb " how & when do I do it, where do I put the camera type.

 Options in Skype show the USB when pluged in but, does not test. 

Nick

---

### Post by linuxyogi on 2011-07-16
> I typed this but it keeps bleenking for 30mnts, is it normal?
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype


You mean Skype doesn't open ? 

I have a Vimicro Webcam which works with Pidgin, Cheese but not with Skype unless I use that workaround. 


> And the " lsusb " how & when do I do it, where do I put the camera type.

 Options in Skype show the USB when pluged in but, does not test. 

Just keep the camera plugged in, open Terminal & type lsusb. Then copy paste the result 

here.  Example

```
$ lsusb 
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 1c4f:0002 SiGma Micro 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


May be someone will reply based on that information.

Best of luck.

---

### Post by nichos on 2011-07-17
SOLVED

Thanx All,

this "$ lsusb " did it & works fine.     .....nick

---

