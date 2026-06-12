---
title: "Huawei E367 USB dongle with Ubuntu 14.04"
date: 2016-03-14
forum: Networking &amp; Wireless
---

### Post by davidbilla on 2016-03-14
Hello everyone,

I haven't been able to find any thread that seems to deal with the Huawei E367 + Ubuntu 14.04 issue satisfactorily; so I'm starting this one.

I am running Ubuntu 14.04 with the kernel **3.19.0-51-generic**. I have been using a Huawei E367 modem with my new Ubuntu 14.04 laptop for the past few months and things have been working fine, although with some glitches. I always had to detach and insert the dongle a few times - sometimes as many as 5 or 6 times - but Ubuntu would always recognise it as a modem in the end. The option **Mobile Broadband** would appear with the name of the connection below it (**8.ta default** - I live in South Africa) when the *Connections* icon at the top right of the desktop is clicked.

All this was until two days ago. From yesterday, connecting the dongle doesn't bring up the **Mobile Broadband** option which normally shows up a few seconds after it is connected. **usb_modeswitch** is installed, but I have never had to do anything manually for the connection to show up. I did not do any software update during the last three days.

lsusb gives the following output:

```
$ lsusb
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 1bcf:28a2 Sunplus Innovation Technology Inc. Dell Integrated Webcam
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
**Bus 001 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. Broadband stick (modem on)**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

... and dmesg brings up the following:

```

[12265.296066] usb 1-1: new high-speed USB device number 5 using xhci_hcd
[12265.426226] usb 1-1: New USB device found, idVendor=12d1, idProduct=1446
[12265.426241] usb 1-1: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[12265.426242] usb 1-1: Product: HUAWEI Mobile
[12265.426244] usb 1-1: Manufacturer: Huawei Technologies
[12265.450241] usb-storage 1-1:1.0: USB Mass Storage device detected
[12265.450339] scsi host12: usb-storage 1-1:1.0
[12265.450477] usb-storage 1-1:1.1: USB Mass Storage device detected
[12265.450534] scsi host13: usb-storage 1-1:1.1
[12266.449057] scsi 12:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[12266.450575] scsi 13:0:0:0: Direct-Access     HUAWEI   TF CARD Storage       PQ: 0 ANSI: 2
[12266.452459] sr 12:0:0:0: [sr1] scsi-1 drive
[12266.452628] sr 12:0:0:0: Attached scsi CD-ROM sr1
[12266.452719] sr 12:0:0:0: Attached scsi generic sg2 type 5
[12266.453043] sd 13:0:0:0: Attached scsi generic sg3 type 0
[12266.457289] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[12266.465974] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 4 ep 2 with no TDs queued?

```

And lsmod gives the following:

```

rtsx_usb_ms            20480  0 
usb_storage            69632  1 uas
memstick               20480  1 rtsx_usb_ms
rtsx_usb_sdmmc         28672  0 
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms

```

**usbserial** used to show up when lsmod was run, but after trying the solution listed here - [http://www.zeroshell.org/forum/viewtopic.php?t=2986]("http://www.zeroshell.org/forum/viewtopic.php?t=2986"), basically adding an entry to E367 in /etc/usb_modeswitch.conf and running usb_modeswitch, it doesn't show up anymore. Also, when I run ```
# usb_modeswitch
``` as root without any options, it brings up the help screen of usb_modeswitch; nothing else.

**usbserial** does show up if I ignored the no result from the usb_modeswitch command and continued on with running ```
modprobe usbserial vendor=0x12d1 product=0x1506
``` but the connection still doesn't show up.

Please let me know if the result of any other command / config file is needed. I would greatly appreciate it if someone could direct me to a solution.

Thanks!

---

