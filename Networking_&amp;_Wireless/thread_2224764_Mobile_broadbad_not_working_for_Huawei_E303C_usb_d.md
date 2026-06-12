---
title: "Mobile broadbad not working for Huawei E303C usb device on Ubuntu 14.04"
date: 2014-05-18
forum: Networking &amp; Wireless
---

### Post by netuser121 on 2014-05-18
I had created a mobile broadband connection in Ubuntu 14.04 and have been connecting to the internet using my Huawei E303C usb device for a few weeks after installing ubuntu 14.04 without installing any additional packages.
However since the last few days the mobile broadband option does not appear after I plug in my device. But the device is being detected as a drive. So I tried installing the Linux drivers provided in it, but no results.
Pl help.

---

### Post by varunendra on 2014-05-21
If the problem still persists, please unplug the modem > wait 10 seconds > replug it > open a terminal (Ctrl-Alt-T) and post back the output of following commands from it -
```
lsusb
dmesg | tail -30
```
While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by netuser121 on 2014-05-28
```
ebin@ebin-HP-Pavilion-g6-Notebook-PC:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b34f Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 005: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ebin@ebin-HP-Pavilion-g6-Notebook-PC:~$ dmesg | tail -30
[ 1073.015984] systemd-udevd[3413]: Failed to apply ACL on /dev/sr1: No such file or directory
[ 1073.016006] systemd-udevd[3413]: Failed to apply ACL on /dev/sr1: No such file or directory
[ 1073.482750] usb 5-2: USB disconnect, device number 4
[ 1081.438778] usb 5-2: new high-speed USB device number 5 using xhci_hcd
[ 1081.458241] usb 5-2: New USB device found, idVendor=12d1, idProduct=1506
[ 1081.458249] usb 5-2: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[ 1081.458254] usb 5-2: Product: HUAWEI Mobile
[ 1081.458259] usb 5-2: Manufacturer: HUAWEI
[ 1081.461588] option 5-2:1.0: GSM modem (1-port) converter detected
[ 1081.461956] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 1081.467372] huawei_cdc_ncm 5-2:1.1: MAC-Address: 58:2c:80:13:92:63
[ 1081.467603] huawei_cdc_ncm 5-2:1.1: cdc-wdm0: USB WDM device
[ 1081.468108] huawei_cdc_ncm 5-2:1.1 wwan0: register 'huawei_cdc_ncm' at usb-0000:00:10.0-2, Huawei CDC NCM device, 58:2c:80:13:92:63
[ 1081.468261] option 5-2:1.2: GSM modem (1-port) converter detected
[ 1081.468467] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 1081.468669] option 5-2:1.3: GSM modem (1-port) converter detected
[ 1081.468829] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 1081.469121] usb-storage 5-2:1.4: USB Mass Storage device detected
[ 1081.469307] scsi8 : usb-storage 5-2:1.4
[ 1081.469552] usb-storage 5-2:1.5: USB Mass Storage device detected
[ 1081.469652] scsi9 : usb-storage 5-2:1.5
[ 1082.468080] scsi 9:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 1082.468285] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 1082.468658] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 1082.470372] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 1082.470389] sr1: scsi-1 drive
[ 1082.470738] sr 8:0:0:0: Attached scsi CD-ROM sr1
[ 1082.470911] sr 8:0:0:0: Attached scsi generic sg3 type 5
[ 1082.651825] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 1082.652462] ISOFS: changing to secondary root


```

---

