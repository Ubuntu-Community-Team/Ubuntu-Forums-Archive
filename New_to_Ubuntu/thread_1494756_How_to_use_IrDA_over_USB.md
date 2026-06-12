---
title: "How to use IrDA over USB ?"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by krtica on 2010-05-27
Please, don't be inpatient and mad. I'm still learning about Ubuntu GNU/Linux. :)

I did try to find online solution. I tried for days, and I tried many things and How-To-s, including some from forum. But I didn't solve anything, so if there is some nice people that are able to help me, please do that. :D 

I'm using Ubuntu 10.04 LTS, desktop, 32-bit.

I have IR-to-USB device. "Mars II, MnMII-898".

When I connect it to USB port, and use **lsusb** command i get this:
```
...
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 009: ID 066f:4210 SigmaTel, Inc. STIr4210 IrDA Bridge**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
...
```

I installed Ircp Tray and realized it doesn't work. :/
As I said, I tried many things. I don't know what to do next. :confused: I'm lost.

After attaching device and use of **dmesg** I have this:
```

...
[ 2228.772126] usb 2-3: new high speed USB device using ehci_hcd and address 10
[ 2228.905866] usb 2-3: configuration #1 chosen from 1 choice
[ 2228.906557] IRDA-USB found at address 10, Vendor: 66f, Product: 4210
[ 2228.907128] irda_usb_parse_endpoints(), And our endpoints are : in=02, out=01 (512), int=00
[ 2228.917439] irda_usb_init_qos(), dongle says speed=0x17F, size=0x20, window=0x8, bofs=0x80, turn=0x4
[ 2228.919503] IrDA: Registered device irda0
[ 2228.919514] usb 2-3: firmware: requesting 42101002.sb
[B][ 2228.924076] STIR421X: Couldn't upload patch
[ 2228.945099] irda-usb: probe of 2-3:1.0 failed with error -2[/B]
[ 2228.945128] ir-usb 2-3:1.0: IR Dongle converter detected
[ 2228.945482] usb 2-3: IR Dongle converter now attached to ttyUSB0
[ 2230.018034] type=1503 audit(1274966644.971:16):  operation="open" pid=2084 parent=2081 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB0"

```
In dev directory I have ttyUSB0, but nothing like **irda0**. Do I have to have it there at all? :confused:

When I started Ircp Tray, it told me to use:

```
sudo irattach /dev/ttyS1 -s
```

so I did, and I found out that it works only if I type:

```
sudo irattach /dev/ttyUSB0 -s
```

But Ircp Tray still don't recognize any device/phone. :/

I found this:
[https://help.ubuntu.com/community/IrdaHowto](https://help.ubuntu.com/community/IrdaHowto)
and this:
[http://ubuntuforums.org/showthread.php?t=963796&highlight=ircp+tray](http://ubuntuforums.org/showthread.php?t=963796&highlight=ircp+tray)

I done it with the difference I used ttyUSB0 instead of ttyS1. (Was it right?)
I realized also that there is */etc/modprobe.d/irda-utils**.conf*** instead of */etc/modprobe.d/irda-utils* file.

After I followed instructions I have this results:

```
user@Ubuntu:/etc$ **sudo /etc/init.d/irda-utils stop**
 * Skipping IrDA service: irattach (not enabled)...                      [ OK ] 
user@Ubuntu:/etc$ **sudo /etc/init.d/irda-utils start**
 * Skipping IrDA service: irattach (not enabled)...                      [ OK ] 
user@Ubuntu:/etc$ **sudo modprobe irda0**
FATAL: Error inserting nsc_ircc (/lib/modules/2.6.32-22-generic-pae/kernel/drivers/net/irda/nsc-ircc.ko): No such device
```

What can I do next? And what did I done wrong? :confused:

*PS: Everything else I have and connect work perfect. This is last issue I have. :/*

---

### Post by krtica on 2010-05-28
I downloaded **4210-4220-4116_Liunx Patch_Files.tar** file from [http://code.google.com/p/s710/issues/detail?id=4#c12](http://code.google.com/p/s710/issues/detail?id=4#c12)
I found 42101002.sb file in archive.

After:
```
sudo cp 42101002.sb /lib/firmware/2.6.32-22-generic-pae/
```

so I finally have:

```
sb 2-3: firmware: requesting 42101002.sb
stir421x_patch_device(): Received firmware 42101002.sb (1687 bytes)
```

...
Still working on this, so if anyone have some idea or advice, I'll be grateful. :D

---

### Post by krtica on 2010-05-29
Next step was editing file:

```
sudo gedit /etc/default/irda-utils
```

and setting DEVICE as:

DEVICE="irda0"

I had also to type in terminal:

```
sudo irattach irda0 -s
```

before i could use Ircp Tray.
Ircp Tray recognized my device.

---

