---
title: "Ubuntu won't detect my USB K3571-Z modem"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by kiwi.paul on 2014-07-17
I admit I'm a linux novice but I'd like to use it more my problem is  that the Disto I like best is Ubuntu and over the last 12 moths I've  installed or tried 3 different versions of Ubuntu (13.04, 12.04 and 12.10) but none of them will  detect my Vodafone K3571-Z USB modem. Modem is approx 2 years old and it  works fine in Windows 7 and now I've just loaded Fedora 19 and it  connected to the internet just fine.

Is their some file I need to download and run in Ubuntu to get it to find my modem.


 Any help will be appreciated.

---

### Post by varunendra on 2014-07-19
Welcome to the forums kiwi.paul!

Please connect your modem > wait for about 30 seconds > open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands -
```
lsusb
dmesg | tail -40
```
..to show us how the modem was detected and whether it changed its mode from 'storage device' to modem.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by kiwi.paul on 2014-07-21
Someone else asked me to do similar so here goes. I've now installed Ubuntu 12.04 on another of my m/c as i was getting tired of waiting for the cd to boot every time.
```
paul@AMDCPU:~$ lsusb 
Bus 001 Device 005: ID 19d2:1010 ZTE WCDMA Technologies MSM (this is the modem)
Bus 003 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

dmesg 
about 10 pages of this but this seesms to be relevant bits


[ 1243.034391] sd 2:0:0:0: [sdb] Write Protect is off 
[ 1243.034396] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00 
[ 1243.034893] sd 2:0:0:0: [sdb] No Caching mode page present 
[ 1243.034898] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[ 1243.040149] sd 2:0:0:0: [sdb] No Caching mode page present 
[ 1243.040155] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[ 1243.081005]  sdb: sdb1 
[ 1243.087523] sd 2:0:0:0: [sdb] No Caching mode page present 
[ 1243.087532] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[ 1243.087536] sd 2:0:0:0: [sdb] Attached SCSI removable disk 
[ 1319.329927] usb 1-6: USB disconnect, device number 3 
[ 1336.852019] usb 1-6: new high-speed USB device number 4 using ehci_hcd 
[ 1336.997250] usb 1-6: New USB device found, idVendor=19d2, idProduct=1009 
[ 1336.997255] usb 1-6: New USB device strings: Mfr=2, Product=1, SerialNumber=3 
[ 1336.997258] usb 1-6: Product: Vodafone Mobile Broadband K3571-Z 
[ 1336.997261] usb 1-6: Manufacturer: Vodafone (ZTE) 
[ 1336.997264] usb 1-6: SerialNumber: P680A8VDFD000000 
[ 1337.002701] scsi3 : usb-storage 1-6:1.0 
[ 1338.003319] scsi 3:0:0:0: CD-ROM            Vodafone  USB SCSI CD-ROM  USB PQ: 0 ANSI: 2 
[ 1338.017920] sr2: scsi-1 drive 
[ 1338.018114] sr 3:0:0:0: Attached scsi CD-ROM sr2 
[ 1338.018240] sr 3:0:0:0: Attached scsi generic sg3 type 5 
[ 1340.273995] usb 1-6: USB disconnect, device number 4 
[ 1345.804023] usb 1-6: new high-speed USB device number 5 using ehci_hcd 
[ 1345.949193] usb 1-6: New USB device found, idVendor=19d2, idProduct=1010 
[ 1345.949197] usb 1-6: New USB device strings: Mfr=2, Product=1, SerialNumber=3 
[ 1345.949201] usb 1-6: Product: Vodafone Mobile Broadband K3571-Z 
[ 1345.949204] usb 1-6: Manufacturer: Vodafone (ZTE) 
[ 1345.949207] usb 1-6: SerialNumber: P680A8VDFD000000 
[ 1345.995026] usbcore: registered new interface driver cdc_wdm 
[ 1346.017153] qmi_wwan 1-6:1.0: not on our whitelist - ignored 
[ 1346.017183] qmi_wwan 1-6:1.1: not on our whitelist - ignored 
[ 1346.017203] qmi_wwan 1-6:1.2: not on our whitelist - ignored 
[ 1346.017223] qmi_wwan 1-6:1.3: not on our whitelist - ignored 
[ 1346.019302] qmi_wwan 1-6:1.4: cdc-wdm0: USB WDM device 
[ 1346.020908] qmi_wwan 1-6:1.4: wwan0: register 'qmi_wwan' at usb-0000:00:02.2-6, Qualcomm WWAN/QMI device, 16:2f:e8:5e:21:4e 
[ 1346.021125] usbcore: registered new interface driver qmi_wwan 
[ 1346.042760] usbcore: registered new interface driver usbserial 
[ 1346.042784] usbcore: registered new interface driver usbserial_generic 
[ 1346.042803] USB Serial support registered for generic 
[ 1346.042809] usbserial: USB Serial Driver core 
[ 1346.055681] usbcore: registered new interface driver option 
[ 1346.055707] USB Serial support registered for GSM modem (1-port) 
[ 1346.055800] option 1-6:1.0: GSM modem (1-port) converter detected 
[ 1346.065019] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0 
[ 1346.065172] option 1-6:1.1: GSM modem (1-port) converter detected 
[ 1346.065336] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1 
[ 1346.065421] option 1-6:1.2: GSM modem (1-port) converter detected 
[ 1346.065562] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2 
[ 1346.065647] option 1-6:1.3: GSM modem (1-port) converter detected 
[ 1346.066795] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB3 


```
Hope it means more to you than it does to me. Thanks in advance.

---

### Post by varunendra on 2014-07-21
> **kiwi.paul said:**
> ```
[ 1346.055707] USB Serial support registered for GSM modem (1-port) 
[ 1346.055800] option 1-6:1.0: GSM modem (1-port) converter detected 
[ 1346.065019] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0 
[ 1346.065172] option 1-6:1.1: GSM modem (1-port) converter detected 
[ 1346.065336] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1 
[ 1346.065421] option 1-6:1.2: GSM modem (1-port) converter detected 
[ 1346.065562] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2 
[ 1346.065647] option 1-6:1.3: GSM modem (1-port) converter detected 
[ 1346.066795] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB3 

```

If there is no "disconnected" message after above in dmesg, it means the device successfully switched its mode and was detected by the OS as a modem. Is it still not available in Network Manager (New Mobile Broadband connection, or previously configured connections showing up)?

Please check "Disk Utility" program. If you see your modem showing up there as a CD, eject it within Disk Utility and recheck Network Manager menu. Sometimes these devices successfully change their mode, but fail to reset by themselves and are stuck in cd/storage mode.

---

### Post by kiwi.paul on 2014-07-23
varunendra I've downloaded a copy of 14.04 and tried that from the cd and it works now I've loaded it instead of my earlier version and I'm inputing this from ubuntu but thanks for you help.

With my old version I would go ito network icon and select the Vodafone connection and it would think about it for a bit and then came back with unable to connect. Now I need to stat learining about using Unix.

Thanks again.

---

### Post by varunendra on 2014-07-23
Glad you sorted it out. :)

Always good to know when things work out-of-box with a new version.

---

