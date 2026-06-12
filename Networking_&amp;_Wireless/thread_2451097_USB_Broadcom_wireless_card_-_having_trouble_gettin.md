---
title: "USB Broadcom wireless card - having trouble getting to work 18.04 LTS"
date: 2020-09-26
forum: Networking &amp; Wireless
---

### Post by dan163 on 2020-09-26
Hey everyone,

Sorry to make another one of these posts but I've done as much reading as I can on this and I think I need to reach out and ask for help.

Bus 001 Device 007: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

Ive install ndiswrapper, and downloaded what I think are the appropriate drivers. 'ndiswrapper -l' gives the following:

bcmwlhigh5 : driver installed
    device (0846:9020) present

however when I 'modprobe ndiswrapper' I get the following errors in dmesg. If someone could take a look and point me in the right direction I would really appreciate it!

[  652.719479] usb 1-5: new high-speed USB device number 7 using ehci-pci
[  652.878664] usb 1-5: New USB device found, idVendor=0846, idProduct=9020, bcdDevice= 0.01
[  652.878666] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  652.878668] usb 1-5: Product: Remote Download Wireless Adapter
[  652.878670] usb 1-5: Manufacturer: Broadcom
[  652.878672] usb 1-5: SerialNumber: 113
[  653.015474] usb 1-5: reset high-speed USB device number 7 using ehci-pci
[  653.180254] ndiswrapper: driver bcmwlhigh5 (ASUS,07/31/2012, 6.30.61.21) loaded
[  653.181858] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[  653.181862] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[  653.181867] ndiswrapper (mp_halt:254): device 0000000093f15faa is not initialized - not halting
[  653.181868] ndiswrapper: device eth%d removed
[  653.181977] ndiswrapper: probe of 1-5:1.0 failed with error -22

---

### Post by CelticWarrior on 2020-09-28
If you value your time you won't waste it with that old piece of crap.

---

### Post by chili555 on 2020-09-29
You will *NOT* get it to work by any means we know of. Please see:

[https://askubuntu.com/questions/899829/wi-fi-adapter-refusing-to-work-netgear-wna3100](https://askubuntu.com/questions/899829/wi-fi-adapter-refusing-to-work-netgear-wna3100)

[https://ubuntuforums.org/showthread.php?t=2264020&highlight=wna3100](https://ubuntuforums.org/showthread.php?t=2264020&highlight=wna3100)

> As of now, unless someone has another driver or process to try, I don't believe this device can be made to work correctly in Ubuntu 14.04 and later. Please don't ask me to help. I've tried everything I know of and it doesn't work.
Sorry.

---

