---
title: "Huawei E3131 Wireless USB Dongle setup"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by Andrew F in Australia on 2014-03-29
HI All,

I've had a USB dongle working for a while, but it recently stopped - was not working at all this morning, intermittently in Windows and not at all in Ubuntu.

As it was 2 years old and a swivel head, I bought a current version - the Huawei E3131

It works perfectly in Windows.

Output from LSUSB

```
horace@horace-HP-ProBook-4730s:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 12d1:14fe Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 002 Device 003: ID 1bcf:2888 Sunplus Innovation Technology Inc. 


```

Text in \etc\modules

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt3592sta
usbserial vendor=0x12d1 product=0x1c07
usbserial vendor=0x12d1 product=0x1506
```

Is anybody able to let me know what I've missed in the setup, as I work in Linux daily with this laptop

Thanks in advance,

AF

---

### Post by praseodym on 2014-03-29
Hi,

this is the storage mode shown in "lsusb". Did you install "usb-modeswitch"?

---

### Post by Andrew F in Australia on 2014-03-29
HI Praseodym,

It's the Huawei wireless dongle.

Using 13.10, the usb_modeswitch command was in the software centre shown as installed. I had some issues understanding the syntax to make it run, however.  Typing "usb_modeswitch" in the terminal window brought up the help screen.  

Are you able to point me to a quick primer to understand the USB Modeswitch syntax?

I also noticed that the address of the Wireless dongle changed when I copied the lsusb settings across yesterday.

Today, I checked and it was:

```
horace@horace-HP-ProBook-4730s:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 002 Device 003: ID 1bcf:2888 Sunplus Innovation Technology Inc. 

```

The 1506 code obviously came up yesterday when I edited the /etc/modules file

---

### Post by praseodym on 2014-03-30
Thats the modem mode. The package modemmanager is buggy in 13.10. You can easily replace it with an older one:
```

sudo apt-get remove --purge modemmanager
```

[http://packages.ubuntu.com/precise/modemmanager](http://packages.ubuntu.com/precise/modemmanager)

Choose 32 or 64 bit, install it and prevent it being updated:
```

echo -e "Package: modemmanager\nPin: version 0.5.2.0*\nPin-Priority: 1000" | sudo tee /etc/apt/preferences.d/modemmanager
```

---

