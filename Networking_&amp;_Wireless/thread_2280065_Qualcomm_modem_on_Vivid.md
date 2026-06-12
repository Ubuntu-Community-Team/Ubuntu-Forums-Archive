---
title: "Qualcomm modem on Vivid"
date: 2015-05-27
forum: Networking &amp; Wireless
---

### Post by hendo2515 on 2015-05-27
I had the internal qualcomm modem working on previous versions of Ubuntu running on my Lenovo T510 but upgrading to Vivid seems to have broken it. Has anyone else had the same issue?

```
rhenderson@mel-prgl001:~$ ls /lib/firmware/gobi/
amss.mbn  apps.mbn  UQCN.mbn

rhenderson@mel-prgl001:~$ lsusb
Bus 002 Device 003: ID 05c6:9204 Qualcomm, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 17ef:480f Lenovo Integrated Webcam [R5U877]
Bus 001 Device 009: ID 04b3:301b IBM Corp. SK-8815 Keyboard
Bus 001 Device 008: ID 04b3:301a IBM Corp. 
Bus 001 Device 007: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 001 Device 010: ID 047f:d055 Plantronics, Inc. 
Bus 001 Device 005: ID 17ef:100a Lenovo ThinkPad Mini Dock Plus Series 3
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

rhenderson@mel-prgl001:~$ usb-devices
T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=05c6 ProdID=9204 Rev=00.02
S:  Manufacturer=Qualcomm Incorporated
S:  Product=Qualcomm Gobi 2000
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

```

---

### Post by hendo2515 on 2015-05-30
I found this entry 

options usbserial vendor=05c6 product=9204

in /etc/modprobe.d/etc-modules-parameters.conf

When I commented it out it worked fine. Feel free to comment on why this would happen and what the entry was in the file?

---

