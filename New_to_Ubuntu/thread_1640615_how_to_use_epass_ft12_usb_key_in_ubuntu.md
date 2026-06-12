---
title: "how to use epass ft12 usb key in ubuntu?"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by yiminghub on 2010-12-08
i need some help
i can not use my epass2000 ft12 usb key in ubuntu
i want to use the hardware in openvpn
but i find some error:
root@dell-desktop:/home/xuyang/openvpn/2.0# lsusb
Bus 002 Device 012: ID 096e:0802 Feitian Technologies, Inc. ePass2000 (G&D STARCOS SPK 2.4)
Bus 002 Device 005: ID 0a5c:5801 Broadcom Corp. 
Bus 002 Device 004: ID 413c:8187 Dell Computer Corp. 
Bus 002 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1814 Ricoh Co., Ltd 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

root@dell-desktop:/home/xuyang/openvpn/2.0# opensc-tool --list-readers
[opensc-tool] reader-pcsc.c:906:pcsc_detect_readers: SCardEstablishContext failed: 0x8010001d
[opensc-tool] reader-pcsc.c:1015:pcsc_detect_readers: returning with: No readers found
Readers known about:
Nr.    Driver     Name
0      openct     CCID Compatible
1      openct     OpenCT reader (detached)

i can't find my epass2000 ft12

thanks.

---

### Post by Sef on 2010-12-09
Moved to ABT.

---

