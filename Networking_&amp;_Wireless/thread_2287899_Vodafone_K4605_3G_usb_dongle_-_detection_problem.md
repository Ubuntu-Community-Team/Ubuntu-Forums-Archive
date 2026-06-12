---
title: "Vodafone K4605 3G usb dongle - detection problem"
date: 2015-07-23
forum: Networking &amp; Wireless
---

### Post by Juhele on 2015-07-23
hi,
I have the Vodafone K4605 3G usb dongle for mobile Internet. However when I plug it in it takes often terribly long time to detect and show in the connection manager so I could use it. After minutes I sometimes replug the device but not sure whether it helps...

lsusb
```
[FONT=monospace][COLOR=#000000]Bus 001 Device 018: ID 12d1:14c6 Huawei Technologies Co., Ltd. [/COLOR][/FONT]
```

dmesg
```
 [FONT=monospace][COLOR=#18b218][23208.260339] [/COLOR][COLOR=#b26818]usb-storage 1-10:1.1[/COLOR][COLOR=#000000]: USB Mass Storage device detected [/COLOR]
[COLOR=#18b218][23208.260555] [/COLOR][COLOR=#b26818]scsi host12[/COLOR][COLOR=#000000]: usb-storage 1-10:1.1 [/COLOR]
[COLOR=#18b218][23209.260675] [/COLOR][COLOR=#b26818]scsi 11:0:0:0[/COLOR][COLOR=#000000]: CD-ROM            Vodafone CD ROM (Huawei)  2.31 PQ: 0 ANSI: 2 [/COLOR]
[COLOR=#18b218][23209.261397] [/COLOR][COLOR=#b26818]scsi 12:0:0:0[/COLOR][COLOR=#000000]: Direct-Access     Vodafone Storage (Huawei)      PQ: 0 ANSI: 2 [/COLOR]
[COLOR=#18b218][23209.263936] [/COLOR][COLOR=#b26818]sr 11:0:0:0[/COLOR][COLOR=#000000]: [sr1] scsi-1 drive [/COLOR]
[COLOR=#18b218][23209.264313] [/COLOR][COLOR=#b26818]sr 11:0:0:0[/COLOR][COLOR=#000000]: Attached scsi CD-ROM sr1 [/COLOR]
[COLOR=#18b218][23209.264657] [/COLOR][COLOR=#b26818]sr 11:0:0:0[/COLOR][COLOR=#000000]: Attached scsi generic sg2 type 5 [/COLOR]
[COLOR=#18b218][23209.268300] [/COLOR][COLOR=#b26818]sd 12:0:0:0[/COLOR][COLOR=#000000]: Attached scsi generic sg3 type 0 [/COLOR]
[COLOR=#18b218][23209.271307] [/COLOR][COLOR=#b26818]sd 12:0:0:0[/COLOR][COLOR=#000000]: [sdb] Attached SCSI removable disk[/COLOR]

[/FONT]
           [FONT=monospace][COLOR=#18b218][23215.335112] [/COLOR][COLOR=#b26818]usb 1-10[/COLOR][COLOR=#000000]: new high-speed USB device number 18 using xhci_hcd [/COLOR]
[COLOR=#18b218][23215.464971] [/COLOR][COLOR=#b26818]usb 1-10[/COLOR][COLOR=#000000]: New USB device found, idVendor=12d1, idProduct=14c6 [/COLOR]
[COLOR=#18b218][23215.464974] [/COLOR][COLOR=#b26818]usb 1-10[/COLOR][COLOR=#000000]: New USB device strings: Mfr=4, Product=3, SerialNumber=0 [/COLOR]
[COLOR=#18b218][23215.464975] [/COLOR][COLOR=#b26818]usb 1-10[/COLOR][COLOR=#000000]: Product: Vodafone Mobile Broadband (Huawei)  [/COLOR]
[COLOR=#18b218][23215.464976] [/COLOR][COLOR=#b26818]usb 1-10[/COLOR][COLOR=#000000]: Manufacturer: Vodafone Group (Huawei)  [/COLOR]
[COLOR=#18b218][23215.466612] [/COLOR][COLOR=#b26818]option 1-10:1.0[/COLOR][COLOR=#000000]: GSM modem (1-port) converter detected [/COLOR]
[COLOR=#18b218][23215.466671] [/COLOR][COLOR=#b26818]usb 1-10[/COLOR][COLOR=#000000]: GSM modem (1-port) converter now attached to ttyUSB0 [/COLOR]
[COLOR=#18b218][23215.466784] [/COLOR][COLOR=#b26818]option 1-10:1.3[/COLOR][COLOR=#000000]: GSM modem (1-port) converter detected [/COLOR]
[COLOR=#18b218][23215.466831] [/COLOR][COLOR=#b26818]usb 1-10[/COLOR][COLOR=#000000]: GSM modem (1-port) converter now attached to ttyUSB1 [/COLOR]
[COLOR=#18b218][23215.466867] [/COLOR][COLOR=#b26818]option 1-10:1.4[/COLOR][COLOR=#000000]: GSM modem (1-port) converter detected [/COLOR]
[COLOR=#18b218][23215.466912] [/COLOR][COLOR=#b26818]usb 1-10[/COLOR][COLOR=#000000]: GSM modem (1-port) converter now attached to ttyUSB2 [/COLOR]
[COLOR=#18b218][23215.466947] [/COLOR][COLOR=#b26818]usb-storage 1-10:1.5[/COLOR][COLOR=#000000]: USB Mass Storage device detected [/COLOR]
[COLOR=#18b218][23215.467014] [/COLOR][COLOR=#b26818]scsi host13[/COLOR][COLOR=#000000]: usb-storage 1-10:1.5 [/COLOR]
[COLOR=#18b218][23215.467089] [/COLOR][COLOR=#b26818]usb-storage 1-10:1.6[/COLOR][COLOR=#000000]: USB Mass Storage device detected [/COLOR]
[COLOR=#18b218][23215.467226] [/COLOR][COLOR=#b26818]scsi host14[/COLOR][COLOR=#000000]: usb-storage 1-10:1.6 [/COLOR]
[COLOR=#18b218][23215.545516] [/COLOR][COLOR=#b26818]usbcore[/COLOR][COLOR=#000000]: registered new interface driver cdc_wdm [/COLOR]
[COLOR=#18b218][23215.660896] [/COLOR][COLOR=#b26818]qmi_wwan 1-10:1.1[/COLOR][COLOR=#000000]: cdc-wdm1: USB WDM device [/COLOR]
[COLOR=#18b218][23215.661007] [/COLOR][COLOR=#b26818]qmi_wwan 1-10:1.1 wwan0[/COLOR][COLOR=#000000]: register 'qmi_wwan' at usb-0000:00:14.0-10, WWAN/QMI device, 56:d[/COLOR]
2:b4:3b:75:9e 
[COLOR=#18b218][23215.661029] [/COLOR][COLOR=#b26818]usbcore[/COLOR][COLOR=#000000]: registered new interface driver qmi_wwan [/COLOR]
[COLOR=#18b218][23216.468125] [/COLOR][COLOR=#b26818]scsi 13:0:0:0[/COLOR][COLOR=#000000]: CD-ROM            Vodafone CD ROM (Huawei)  2.31 PQ: 0 ANSI: 2 [/COLOR]
[COLOR=#18b218][23216.468770] [/COLOR][COLOR=#b26818]scsi 14:0:0:0[/COLOR][COLOR=#000000]: Direct-Access     Vodafone Storage (Huawei)      PQ: 0 ANSI: 2 [/COLOR]
[COLOR=#18b218][23216.470352] [/COLOR][COLOR=#b26818]sr 13:0:0:0[/COLOR][COLOR=#000000]: [sr1] scsi-1 drive [/COLOR]
[COLOR=#18b218][23216.470443] [/COLOR][COLOR=#b26818]sr 13:0:0:0[/COLOR][COLOR=#000000]: Attached scsi CD-ROM sr1 [/COLOR]
[COLOR=#18b218][23216.470723] [/COLOR][COLOR=#b26818]sr 13:0:0:0[/COLOR][COLOR=#000000]: Attached scsi generic sg2 type 5 [/COLOR]
[COLOR=#18b218][23216.470907] [/COLOR][COLOR=#b26818]sd 14:0:0:0[/COLOR][COLOR=#000000]: Attached scsi generic sg3 type 0 [/COLOR]
[COLOR=#18b218][23216.474356] [/COLOR][COLOR=#b26818]sd 14:0:0:0[/COLOR][COLOR=#000000]: [sdb] Attached SCSI removable disk[/COLOR][/FONT]
```

the [FONT=monospace][COLOR=#000000]**usb-modeswitch-data** package is already installed. Is there any way to somehow manually switch the device to usb serial or any other solution which could make the initialization a little bit quicker?

thanks
[/COLOR][/FONT]

---

